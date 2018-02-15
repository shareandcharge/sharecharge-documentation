==========
Components
==========

EV Charging Network
===================

* Running in a consortium PoA network.
* Smart contracts business logic for charging mgmt.
* Token system (ev, ewf, others).

Core Client
===========

* Reference client for s&c net, written in typescript.
* Provides charging services.
* Wallet by eth client.
* Setup/conf via cmd, gui...
* Operates the charging via bridges.

Bridges
=======

* Comm with modbus, ocpp, ocpi, vendor apis.
* Should be a pluggable system (e.g. django packages).
* Includes a mock backend to test a bridge

Library
=======

* Reference implementation in Typescript/JS.
* Used by both core client and ev dapps.
* New features available in this lib.

EV Dapps
========

* Consumers of s&c: users via smartphones w/ iOS, android, pwa clients, headless clients, embedded soft into evs using our sdk, framework plugins...
* Provides ui/ux to operate the charging solution.
* Different implementations (e.g. metamask web, ionic, native apps, plugins for waze/gmaps, etc).
* Wallets from libs, metamask, etc.
* Usually only sign tx, then send to eth node for bradcasting.
* SDK to integrate our solution into existing solutions.
