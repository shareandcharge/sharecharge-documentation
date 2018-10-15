========
REST API
========

**Collection of endpoints that wrap the S&C functionality for front-ends, GUIs and other components to connect to.**

Overview
========

The **REST API** allows interacting with the features from Share&Charge by using the HTTP protocol. Front-ends can be thus built to present Backoffices and dashboards, and also other services or microservices can be plugged. The preferred way to expose this API is using the **Core Client**, but in theory this API can be used on any deployment/system.

MSPs will usually plug their applications to Share&Charge via RESTful API **endpoints** from an S&C API. An exception to this scenario could perhaps be a MSP Dapp that relies solely on a business logic managed in the browser entirely. In this case the Dapp would be using directly the S&C JavaScript Library.

Likewise, CPOs may also build front-end User Interfaces that consume the S&C API so that tools such as control panels, monitor systems or Backoffices can be presented to system administrators, operators or other staff members to easily provision and maintain the charging infrastructure on the EV Charging Network.

In a Nutshell
=============

* **Deploy MSP contracts** and **mint tokens for drivers**
* **Provision locations** on the network
* **Find locations** and **initiate charging sessions** for testing 

Install and Usage
=================

The S&C API comes with Core Client installations. It can also be installed standalone ::

    npm install -g @motionwerk/sharecharge-api

This exposes a binary which will run the HTTP server, with optional environment variables to configure the host and port ::

    HOST=0.0.0.0 PORT=6001 sc-api

The API also serves a documentation server, available at ``http://localhost:3000/api/docs`` by default.