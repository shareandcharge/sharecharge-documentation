===========
Core Client
===========

**Application service listening to the EV Charging Network to allow communication between S&C user agents.**

Overview
========

The **Core Client** is a "batteries included" solution that allows partners to easily **download, setup an run a server** that can be deployed on-premises in CPOs or MSPs facilities, or inside Charging Stations in a more *IoT* approach.

Once running as a service, the *Core Client* **listens for events** in the Blockchain, to facilitate the execution of **charging sessions** and recording the information from the resulting *Charge Detail Records*.

The Core Client is an **essential piece** of the *Share&Charge Platform*, as it serves two additional functions, apart from the one mentioned above:

* It serves as provider of **S&C Bridges** for intercommunication with charging infrastructure from CPOs or directly to a Charging Station.
* It can be used to host the **S&C ReST API** so that front-ends and other consumers use it to create User Interfaces for Backoffices and dashboards, or connect to microservices.

In a Nutshell
=============

* **Reference client** to operate through the *EV Charging Network*.
* **Listens for events** all the time (24/7), because it's a daemon process.
* **Extensible integration** of *Charging Points* from new *CPOs* or *IoT* ready poles by using **Bridges** (plugin system).
* **HTTP Server** of the *S&C ReST API* to connect front-ends or other systems to the Core Client.
