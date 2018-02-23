=========================
Core Client Configuration
=========================

The Share & Charge Core Client supports multiple configuration values. Options can be specified when running the Core Client or else a configuration file can be used. 

Provisioning your config file 
=============================

An example ``conf.yaml`` is provided in the Core Client root directory::

    --- 
      statusInterval: 5000
      connectorData: ./connectors.json
      test: false
      bridge: ./testBridge1

TOML can also be used::

    statusInterval = 5000
    connectorData = "./connectors.json"
    test = false
    bridge = "./testBridge1"

The configuration file can be invoked by using the ``--config`` flag::

    sc client --config conf.yaml

Otherwise, command line options can be used as usual and will overwite values in the config file::

    sc client --config conf.yaml --status-interval 5000



Configuration Values
====================

``connectors``
------------------
The path to the JSON file containing connector information. This is used to register connectors on the S&C EV Network.

Example ``connectors.json``::

    {
      "0x01": {
        "id": "0x01",
        "client": "0x01",
        "owner": "EVC Ltd",
        "lat": "52.8",
        "lng": "-0.6",
        "price": 1,
        "model": 1,
        "plugType": 2,
        "openingHours": "0024002400240024002400240024",
        "isAvailable": true
      }
    }

``status-interval``
--------------------------
The time to wait between intervals when requesting connector availability updates from the bridge.

``test``
--------
Mock the Ethereum smart contracts used by the S&C EV Network.

``bridge``
----------
The path to the bridge class.


