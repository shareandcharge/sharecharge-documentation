============================
Command Line Interface (CLI)
============================

**Mid-level approach that uses the S&C Library to expose commands that perform operations on the EV Network.**

Overview
========

The **Command Line Interface (CLI)** is the perfect tool for advanced users to interact and operate in the **EV Charging Network** straight from the terminal. **CP Owners** can deploy and manage their Charging Point assets, while **EV Users** access the network to browse, discover and use such assets.

This is a mid-level approach to provide an interface for advanced users that want flexibility when accessing and operating with the platform. The CLI must aim to become the swiss army knife for developers, systems administrators or any breed of command line dwellers. Furthermore, it will enable automation through scripts or other advanced tools for deployment, testing, or Quality Assurance.

In a Nutshell
=============

* **Setup and configure** the Share & Charge software stack
* **Deploy MSP contracts** and **mint tokens for drivers**
* **Provision locations** on the network
* **Find locations** and **initiate charging sessions** for testing 

Install and Usage
=================

The CLI is available as an NPM package: ::

    npm install -g @motionwerk/sharecharge-cli

Six key modules are provided as subcommands, these being S&C software stack configuration, data provisioning, charge session access, wallet and token management, and charge detail record indexing. They can be initiated, for example, in the following way: ::

    sc-cli wallet balance

Help can be provided on the top level, or for individual subcommands: ::

    sc-cli -h
    sc-cli token -h