Contracts Specification
=======================

.. contents::
   :local:

See `sharecharge-contracts <https://github.com/motionwerkGmbH/sharecharge-contracts>`__

+-------------------+--------------------------------------------------------+
| Name              | Description                                            |
+-------------------+--------------------------------------------------------+
| ChargingStation   | Core start/stop business logic for CPOs, private       |
|                   | stations owners and connector controllers. 	     |
+-------------------+--------------------------------------------------------+
| StationStorage    | Stores all connector information.                      |
+-------------------+--------------------------------------------------------+
| ChargingSessions  | Stores connector session state information.            |
+-------------------+--------------------------------------------------------+
| EVCoin            | Token required to charge at stations on the network.   |
|                   | Implements MintableToken                               |
+-------------------+--------------------------------------------------------+
| Restricted        | Grants certain addresses access to methods which       |
|                   | implement it.                                          |
+-------------------+--------------------------------------------------------+
| MintableToken     | Open Zeppelin audited token allowing minting.          |
+-------------------+--------------------------------------------------------+

ChargingStation
---------------

*Methods*

+-----------+--------------------------------+------------+-----------+
| Name      | Inputs                         | Events     | Sender    |
|           |                                | (outputs)  |           |
+===========+================================+============+===========+
| construct | ``address`` StationStorage,    |            | owner     |
| or        | ``address`` ChargingSessions,  |            |           |
|           | ``address`` EVCoin             |            |           |
+-----------+--------------------------------+------------+-----------+
| requestSt | ``bytes32`` connectorId        | StartReque | controlle |
| art       |                                | sted       | r         |
+-----------+--------------------------------+------------+-----------+
| requestSt | ``bytes32`` connectorId        | StopReques | controlle |
| op        |                                | ted        | r         |
+-----------+--------------------------------+------------+-----------+
| confirmSt | ``bytes32`` connectorId,       | StartConfi | connector |
| art       | ``address`` controller         | rmed       | owner     |
+-----------+--------------------------------+------------+-----------+
| confirmSt | ``bytes32`` connectorId        | StopConfir | connector |
| op        |                                | med        | owner     |
+-----------+--------------------------------+------------+-----------+
| logError  | ``bytes32`` connectorId,       | Error      | connector |
|           | ``uint8`` errorCode            |            | owner     |
+-----------+--------------------------------+------------+-----------+

*Events (outputs)*

+-----------------------+-----------------------+-----------------------+
| Name                  | Indexed parameters    | Subscriber            |
+=======================+=======================+=======================+
| StartRequested        | ``bytes32``           | connector owner       |
|                       | connectorId,          |                       |
|                       | ``address``           |                       |
|                       | controller            |                       |
+-----------------------+-----------------------+-----------------------+
| StopRequested         | ``bytes32``           | connector owner       |
|                       | connectorId,          |                       |
|                       | ``address``           |                       |
|                       | controller            |                       |
+-----------------------+-----------------------+-----------------------+
| StartConfirmed        | ``bytes32``           | controller            |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+
| StopConfirmed         | ``bytes32``           | controller            |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+
| Error                 | ``bytes32``           | controller            |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+

*Error Codes*

+------+---------------------------+
| Code | Error                     |
+======+===========================+
| 0    | Start failed on connector |
+------+---------------------------+
| 1    | Stop failed on connector  |
+------+---------------------------+

StationStorage
--------------

*Methods*

+-----------------------+-----------------------+-----------------------+
| Name                  | Inputs                | Outputs               |
+=======================+=======================+=======================+
| connectors            | ``bytes32``           | ``address`` owner,    |
|                       | connectorId           | ``bool`` isAvailable, |
|                       |                       | ``bool`` isVerified   |
+-----------------------+-----------------------+-----------------------+
| registerConnector     | ``bytes32``           |                       |
|                       | connectorId, ``bool`` |                       |
|                       | isAvailable           |                       |
+-----------------------+-----------------------+-----------------------+
| verifyConnector       | ``bytes32``           |                       |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+
| setAvailability       | ``bytes32``           |                       |
|                       | connectorId, ``bool`` |                       |
|                       | isAvailable           |                       |
+-----------------------+-----------------------+-----------------------+
| isAvailable           | ``bytes32``           | ``bool`` isAvailable  |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+
| isVerified            | ``bytes32``           | ``bool`` isVerified   |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+
| getOwner              | ``bytes32``           | ``address`` owner     |
|                       | connectorId           |                       |
+-----------------------+-----------------------+-----------------------+

.. _chargingsessions-1:

ChargingSessions
----------------

*Methods*

+------+-------------------------------------------------+-----------------------+
| Name | Inputs                                          | Outputs               |
+======+=================================================+=======================+
| set  | ``bytes32`` connectorId, ``address`` controller |                       |
+------+-------------------------------------------------+-----------------------+
| get  | ``bytes32`` connectorId                         | ``address`` connector |
+------+-------------------------------------------------+-----------------------+

EVCoin
------

*Methods* - See
`MintableToken <https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/token/ERC20/MintableToken.sol>`__

+-----------------------+-----------------------+-----------------------+
| Name                  | Inputs                | Outputs               |
+=======================+=======================+=======================+
| constructor           | ``uint256``           |                       |
|                       | initialSupply         |                       |
+-----------------------+-----------------------+-----------------------+
| restrictedApproval    | ``address`` from,     | Approval              |
|                       | ``address`` to,       |                       |
|                       | ``uint256`` value     |                       |
+-----------------------+-----------------------+-----------------------+
