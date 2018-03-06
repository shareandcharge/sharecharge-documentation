============================
Command Line Interface (CLI)
============================

**TODO short description**

The **Command Line Interface (CLI)** is the perfect tool for advanced users to interact and operate in our **EV Charging Network** straight from your terminal. **CP Owners** can deploy and manage their Charging Point assets, while **EV Users** access the network to browse, discover and use such assets.

Each implementation of a CLI will make use of its correspondent implementation of **EV Network Client Library**. For instance, the *Node.js* based CLI will use the *Node.js* EV Library. Different flavour are delivered, in order to best suit different needs for different environments or application stacks.

To install the cli you have to use::

    npm link

Charge Point on EV Network Subcommand Usage::

    sc cp --help
    Usage: sc cp <command> [options]

    Commands:
      sc cp status [id]           Returns the current status of the Charge Point with given id
      sc cp info [id]             Returns the current info of the Charge Point with given id
      sc cp disable [id]          Disables the Charge Point with given id
      sc cp enable [id]           Enables the Charge Point with given id
      sc cp register [id]         Registers a Charge Point with given id in the EV Network
      sc cp start [id] [seconds]  Start a charging session at a given Charge Point

    Options:
      --json         generate json output
      -v, --version  Show version number                                   [boolean]
      -h, --help     Show help                                             [boolean]

Example::

    sc cp register 0x01
    Registering CP with id: 0x01 for client: 0x09
    Success: true
    Tx: 0xc55409b655a829f1b5d7631f9dde219538c9fbf60c347bf222e0f82cc19fb2b3
    Block: 156334

    sc cp start 0x01
    Starting charge on 0x01 for 10 seconds...
    Start request by 0xf2035405c983638c6d560d43ce199240f6bf135d included in block 156362
    Start confirmation included in block 156364
    Charging [================================================================================] 10s
    Stop confirmation included in block 156376

Charge Point on Bridge Subcommand Usage::

    sc bridge --help
    Usage: sc bridge <command> [options]

    Commands:
      sc bridge status  Returns the current status of the configured Bridge

    Options:
      --json         generate json output
      -v, --version  Show version number                                   [boolean]
      -h, --help     Show help                                             [boolean]

Example::

    sc bridge status 0x12
    Getting status of bridge.
    Bridge Available: true
    Bridge name: test2


Client Subcommand Usage::

    sc client --help
    Usage: sc client [options]

    Options:
      --json             generate json output
      --config           Path to plaintext config file
      --id               The client ID used to filter EV charge requests    [string]
      --pass             The password of the user's Ethereum address for confirming
                         charge sessions                      [string] [default: ""]
      --bridge           Path to the bridge which the Core Client should connect to
                                                                            [string]
      --connectors       Path to the connector data if registration of connectors
                         required                                           [string]
      --test             Use a mock S&C EV ChargingStation contract        [boolean]
      --status-interval  Specify interval between connector status updates from
                         bridge                            [number] [default: 30000]
      -v, --version      Show version number                               [boolean]
      -h, --help         Show help                                         [boolean]

Example::

    sc client
    2018-03-06T14:48:46.803Z - warn: No Client ID found in configuration!
    2018-03-06T14:48:46.805Z - warn: No Ethereum password found in configuration!
    2018-03-06T14:48:46.841Z - debug: Type of contract: Contract
    2018-03-06T14:48:46.846Z - info: Configured to update every 30000ms
    2018-03-06T14:48:46.846Z - debug: Bridge status: true
    2018-03-06T14:48:46.847Z - info: Core Client connected to test1 bridge
    2018-03-06T14:48:46.847Z - info: Listening for events...
