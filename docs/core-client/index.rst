===========
Core Client
===========

**Application service listening to the EV Charging Network to allow communication between S&C user agents.**

Overview
========

The **Core Client** is a "batteries included" solution that allows partners to easily **download, setup an run a server** that can be deployed on-premises in CPO facilities, or inside Charging Stations in a more *IoT* approach.

Once running as a service, the *Core Client* **listens for events** on the Blockchain, to facilitate the execution of **charging sessions** and recording the information from the resulting *Charge Detail Records*.

The Core Client is an **essential piece** of the *Share&Charge Platform*, as it serves two additional functions, apart from the one mentioned above:

* It serves as provider of **S&C Bridges** for intercommunication with charging infrastructure from CPOs or directly to a Charging Station.
* It can be used to host the **S&C ReST API** so that front-ends and other consumers use it to create User Interfaces for Backoffices and dashboards, or connect to microservices.

In a Nutshell
=============

* **Reference client** to operate through the *EV Charging Network*.
* **Listens for events** all the time (24/7), because it's a daemon process.
* **Extensible integration** of *Charging Points* from new *CPOs* or *IoT* ready poles by using **Bridges** (plugin system).
* **HTTP Server** of the *S&C REST API* to connect front-ends or other systems to the Core Client.

Install and Usage
=================

The reference implementation of the S&C Core Client is available as an NPM package: ::

    npm install -g @motionwerk/sharecharge-core-client

The Core Client must first be configured. The official `S&C command line interface`_ (CLI) can be used to manage configuration settings, however it is also possible to have the Core Client configure itself before launch: ::

    sc-cc init

.. _S&C command line interface: ../cli/index.html

This will provision a configuration file in ``$HOME/.sharecharge/`` with default values, including an Ethereum RPC provider, an IPFS provider and test stage contracts.

Running the Core Client is simple: ::

    sc-cc start

It is first essential to add locations and tariffs to the network (this can easily be done through the CLI). The Core Client will then begin to listen for specific events relating to the account owner's locations. Also note that the Core Client uses a simulation/mock bridge by default. `Official Share & Charge bridges`_ are available to be used as plugins for the Core Client. 

.. _Official Share & Charge bridges: ../bridges/index.html

By default the Core Client does not expose the `S&C REST API`_. This can be done with additional configuration: ::

    sc-cc start --api --api-host=0.0.0.0 --api-port=3001

.. _S&C REST API: ../rest-api/index.html
