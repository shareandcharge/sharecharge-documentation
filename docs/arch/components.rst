==========
Components
==========

EV Charging Network
===================

* Running in a consortium PoA network.
* Smart contracts business logic for charging mgmt.
* Token system (ev, ewf, others).

EV Network Client Libraries
===========================

Our Client Libraries allow a **programmatic access** to all the functionality implemented in the **EV Charging Network**, such as:

* **CP Owners** provisioning their **Charging Points** to be accessible by the rest of Share&Charge users (usually with convenience tools such as our **S&C Command Line Interface)**
* **EV Users** accessing the network to discover, evaluate and request new charging processes from the existing offer of **Charging Points**.

Initially, interacting with our smart contracts involves communicating to a node through RPC calls (using **Web3**). This can be sometimes cumbersome to learn and implement. Thus, to make coding against these **easier**, Share&Charge provides client libraries in **different languages** that reduce this friction and empower developers to focus on making robust products and services on top of our platform.

Featured Libraries
------------------

* JavaScript: TODO link to docs
* Python: TODO link to docs

Core Client
===========

* Reference client for s&c net, written in typescript.
* Provides charging services.
* Wallet by eth client.
* Setup/conf via cmd, gui...
* Operates the charging via bridges.

Command Line Interface (CLI)
============================

The **Command Line Interface (CLI)** is the perfect tool for advanced users to interact and operate in our **EV Charging Network** straight from your terminal. **CP Owners** can deploy and manage their Charging Point assets, while **EV Users** access the network to browse, discover and use such assets.

Each implementation of a CLI will make use of its correspondent implementation of **EV Network Client Library**. For instance, the *Node.js* based CLI will use the *Node.js* EV Library. Different flavour are delivered, in order to best suit different needs for different environments or application stacks.

Bridges
=======

* Comm with modbus, ocpp, ocpi, vendor apis.
* Should be a pluggable system (e.g. django packages).
* Includes a mock backend to test a bridge

EV Dapps
========

* Consumers of s&c: users via smartphones w/ iOS, android, pwa clients, headless clients, embedded soft into evs using our sdk, framework plugins...
* Provides ui/ux to operate the charging solution.
* Different implementations (e.g. metamask web, ionic, native apps, plugins for waze/gmaps, etc).
* Wallets from libs, metamask, etc.
* Usually only sign tx, then send to eth node for bradcasting.
* SDK to integrate our solution into existing solutions.
