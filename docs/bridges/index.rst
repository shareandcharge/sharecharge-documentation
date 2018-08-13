===========
CPO Bridges
===========

**Modules that provide connectivity between the Core Client and the CPO charging infrastruture.**

Overview
========

The **CPO Bridges** are the **connection points** between the Charging Stations and our EV Charging Network. These are run by the Core Client, and enable it to communicate, back and forth, the charging sessions that EV Drivers initiate with the Charging Station responsible of delivering the electricity that is promised in the energy transaction.

Thus, CPOs use the Bridges to connect the Core Client instance to a Charging Station. There are two possible setups:

* Through a **CPO Backend**: formally called *CSMS (Charging Station Management System)*, these expose an API to enable the remote operations of the infrastructure, usually controlling thousands of stations. The following are supported:
  * Via **OCPI**: Industry standard.
  * Via **Proprietary API**: Developed in-house by the CPO, each one exposing different features, endpoints, data exchange formats, etc.
* Directly to a **Charging Station**: 
  * Via **OCPP**: Industry standard, widely adopted by many CPOs.
  * Via **Charging Controllers**: with the Core Client directly embedded in an IoT Charging Station, Bridges are developed for communications protocols such as *ModBus*.

In a Nutshell
=============

* **Proxy** between CPO and EV Charging Network using protocols such OCPP, OCPI, proprietary APIs or direct communications protocols such as ModBus.
* **Pluggable system** that can be extended over time with as many integrations with CPO APIs as needed.
* **Mock bridge** should be included to help developers build and test functionality without having to set up a real API.
