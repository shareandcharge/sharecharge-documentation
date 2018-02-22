=========================
Core Client Configuration
=========================

The Share & Charge Core Client supports multiple configuration values. Options can be specified when running the Core Client or else a configuration file can be used. 

Provisioning your config file 
=============================

An example ``conf.yaml`` is provided in the Core Client root directory::

    --- 
      statusUpdateInterval: 5000
      connectorData: ./connectors.json
      test: false
      
      bridge:
        name: Bridge
        path: ./testBridge1


TOML can also be used::

    statusUpdateInterval = 5000
    connectorData = "./connectors.json"
    test = false
    
    [bridge]
    name = "Bridge"
    path = "./testBridge.ts"

The configuration file can be invoked by using the ``--config`` flag::

    sc client --config conf.yaml

Otherwise, command line options can be used as usual::

    sc client --test=false --status-update-interval 5000



Configuration Values
====================

``connector-data``
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

``status-update-interval``
--------------------------
The time to wait between intervals when requesting connector availability updates from the bridge.

``test``
--------
Mock the Ethereum smart contracts used by the S&C EV Network.


``bridge``
----------

``name``
^^^^^^^^
The name of the bridge class.

``path``
^^^^^^^^
The path to the bridge class.


