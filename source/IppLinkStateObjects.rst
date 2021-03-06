IppLinkState Object
=============================================================

*state/IppLink*
------------------------------------

- Multiple objects of this type can exist in a system.

+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
|      **PARAMETER NAME**      | **DATA TYPE** |        **DESCRIPTION**         | **DEFAULT** |        **VALID VALUES**        |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| DrNameRef **[KEY]**          | string        | A human-readable text string   | N/A         | N/A                            |
|                              |               | containing the Distributed     |             |                                |
|                              |               | Relay Instance name to which   |             |                                |
|                              |               | this IPP is associated         |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| IntfRef **[KEY]**            | string        | A human-readable text          | N/A         | N/A                            |
|                              |               | string containing a locally    |             |                                |
|                              |               | significant name for the       |             |                                |
|                              |               | Distributed Relay IPP port     |             |                                |
|                              |               | link                           |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| DRCPDUsRx                    | uint64        | The number of valid DRCPDUs    | N/A         | N/A                            |
|                              |               | received on this IPP.          |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| DRCPDUsTx                    | uint64        | The number of DRCPDUs          | N/A         | N/A                            |
|                              |               | transmitted on this IPP.       |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| DiffPortalReason             | string        | A human-readable text string   | N/A         | N/A                            |
|                              |               | indicating the most recent     |             |                                |
|                              |               | set of variables that are      |             |                                |
|                              |               | responsible for setting the    |             |                                |
|                              |               | variable Differ_Portal or      |             |                                |
|                              |               | Differ_Conf_Portal (9.4.8) on  |             |                                |
|                              |               | this IPP to TRUE               |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| IPPID                        | uint32        | The unique identifier          | N/A         | N/A                            |
|                              |               | allocated to this IPP by the   |             |                                |
|                              |               | local Portal System. This      |             |                                |
|                              |               | attribute identifies an IPP    |             |                                |
|                              |               | instance among the subordinate |             |                                |
|                              |               | managed objects of the         |             |                                |
|                              |               | containing object.             |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| LastRxTime                   | uint32        | The time at which the last     | N/A         | N/A                            |
|                              |               | DRCPDU was received by this    |             |                                |
|                              |               | IPP                            |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| PortConversationPasses       | uint8         | A read-only current            | N/A         | N/A                            |
|                              |               | operational vector of Boolean  |             |                                |
|                              |               | values                         |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| DRCPRxState                  | int32         | This attribute holds the value | N/A         | CURRENT(0), INITIALIZE(3),     |
|                              |               | current if the DRCPDU Receive  |             | EXPIRED(1), DEFAULTED(2),      |
|                              |               | state machine for the IPP is   |             | REPORT_TO_MANAGEMENT(4)        |
|                              |               | in the CURRENT state           |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+
| GatewayConversationDirection | uint8         | A read-only current            | N/A         | N/A                            |
|                              |               | operational vector of Boolean  |             |                                |
|                              |               | values                         |             |                                |
+------------------------------+---------------+--------------------------------+-------------+--------------------------------+



*OpxFlexSwitch CURL API Supported*
------------------------------------

	- GET By Key
		 curl -X GET -H 'Content-Type: application/json' --header 'Accept: application/json' -d '{<Model Object as json-Data>}' http://device-management-IP:8080/public/v1/state/IppLink
	- GET ALL
		 curl -X GET http://device-management-IP:8080/public/v1/state/IppLinks?CurrentMarker=<x>&Count=<y>
	- GET By ID
		 curl -X GET http://device-management-IP:8080/public/v1/config/IppLinkState/<uuid>


*OpxFlexSwitch SDK API Supported:*
------------------------------------



- **GET**


::

	import sys
	import os
	from opxflexswitchV2 import OpxFlexSwitch

	if __name__ == '__main__':
		switchIP := "192.168.56.101"
		swtch = OpxFlexSwitch (switchIP, 8080)  # Instantiate object to talk to flexSwitch
		response, error = swtch.getIppLinkState(DrNameRef=drnameref, IntfRef=intfref)

		if error != None: #Error not being None implies there is some problem
			print error
		else :
			print 'Success'


- **GET By ID**


::

	import sys
	import os
	from opxflexswitchV2 import OpxFlexSwitch

	if __name__ == '__main__':
		switchIP := "192.168.56.101"
		swtch = OpxFlexSwitch (switchIP, 8080)  # Instantiate object to talk to flexSwitch
		response, error = swtch.getIppLinkStateById(ObjectId=objectid)

		if error != None: #Error not being None implies there is some problem
			print error
		else :
			print 'Success'




- **GET ALL**


::

	import sys
	import os
	from opxflexswitchV2 import OpxFlexSwitch

	if __name__ == '__main__':
		switchIP := "192.168.56.101"
		swtch = OpxFlexSwitch (switchIP, 8080)  # Instantiate object to talk to flexSwitch
		response, error = swtch.getAllIppLinkStates()

		if error != None: #Error not being None implies there is some problem
			print error
		else :
			print 'Success'


