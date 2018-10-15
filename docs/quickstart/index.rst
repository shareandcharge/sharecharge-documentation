End-to-End Quickstart
=======================

The following software should be installed: 
* `sharecharge-cli`_: Provision charging tokens, provision locations and request charging sessions
* `sharecharge-core-client`_: Listen for charging requests and manage current sessions

.. _sharecharge-cli: ../cli/index.html
.. _sharecharge-core-client: ../core-client/index.html

This quickstart will show how to setup a complete end-to-end charging scenario using MSP, Driver and CPO operations. For the sake of simplicity, one wallet will perform all actions. 

If not already, install the CLI and Core Client: ::

    $ npm install -g @motionwerk/sharecharge-cli @motionwerk/sharecharge-core-client

First of all, generate a new wallet and save it: ::

    $ sc-cli wallet generate
    Wallet created. Update the seed in your configuration to use.
    coinbase: 0x3f949e345f5baa580d3fb406667216b544cc87ae
    seed:     melt history save fuel monster recipe urban clump slam purity wonder just

    $ sc-cli config set seed "melt history save fuel monster recipe urban clump slam purity wonder just"

The newly created wallet needs "infrastructure coins". These are the coins that run the network, i.e. they pay for the functionality provided by authorities in the network. By default the CLI is configured to use a test network - as such these infrastructure coins are not tied to any fiat currency. Coins can be requested at a faucet_ in the case of these test networks. 

.. _faucet: http://tobalaba.slock.it/faucet/

Once these coins have been received, the CPO should add locations_ and tariffs_ to the network. Note that the data format must comply with OCPI. A template is provided in ``$HOME/.sharecharge/locations.json`` and ``tariffs.json``. Once they have been edited, they may be added: ::

    $ sc-cli store add-locations
    $ sc-cli store add-tariffs

.. _locations: https://github.com/ocpi/ocpi/blob/master/mod_locations.md#3-object-description
.. _tariffs: https://github.com/ocpi/ocpi/blob/master/mod_tariffs.md#3-object-description

If successful, the IPFS receipt will be shown in the output. It is also possible to confirm the successful addition of locations and tariffs: ::

    $ sc-cli store get-locations
    $ sc-cli store get-tariffs

In the background, the Core Client can be run and should display the wallet's coinbase (primary account) and the S&C ID of the first location added: ::

    $ sc-cc start
    Connected to bridge: MockBridge
    Coinbase: 0x2f7d42e9f5112a2999c968a45c26aec13c5acb06
    Listening for events on 1 locations (head: 0x2d33312e3933373331382c3131352e373535373939)

The last aspect necessary to start a charging session is charging tokens. It is the role of the MSP to provision their own token contract which they can use to manage driver token funds. Deploy a token contract and store it: ::

    $ sc-cli token deploy
    New contract created at address 0x3F08d1D29a8Bbfbba2867169447352dC101DaCD4
    Save this address in your config under "tokenAddress" to use it

    $ sc-cli config set tokenAddress 0x3F08d1D29a8Bbfbba2867169447352dC101DaCD4

Now that the S&C CLI is configured to use the new MSP token contract, tokens can be minted for the driver wishing to initiate a charging session: ::

    $ sc-cli token mint

Follow the instructions to mint tokens for the address of the wallet created at the start. (Run ``sc-cli wallet info`` to see it again). Note that one token is equivalent to one decimal unit of currency, according to the currency specified in the tariff. For example, if a "EUR" tariff has been added with a single price component of 0.90€ per hour, and a driver wishes to charge for 2 hours, it is necessary that 180 tokens are held by the driver before the start of the charging session. 

If all was successful, it is now possible to start a simulated charging session. ::

    $ sc-cli charging request-start

Follow the instructions, specifying a location ID (e.g. ``0x2d33312e3933373331382c3131352e373535373939``, as above) to get started. After a succesful start request, the Core Client should respond, stating that it has confirmed the session on the network: ::

    Calling bridge to start session on BB-5983-3
    Bridge: startRemoteTransaction - 02482808578
    Started BB-5983-3 session 02482808578 via bridge
    Confirmed BB-5983-3 start success on network
    
The bridge includes a session manager, which will automatically stop the session after its conditions (duration or consumption) have been met. ::

    Manager: 02482808578 - {"consumption":250,"duration":10,"terminated":false}
    Consumption: 250 / 10000
    Manager: 02482808578 - {"consumption":500,"duration":20,"terminated":false}
    Consumption: 500 / 10000

Otherwise, the charge can be manually stopped by the driver: ::

    $ sc-cli charging request-stop