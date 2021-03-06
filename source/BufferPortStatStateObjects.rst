BufferPortStatState Object
=============================================================

*state/BufferPortStat*
------------------------------------

- Multiple objects of this type can exist in a system.

+--------------------+---------------+--------------------------------+-------------+------------------+
| **PARAMETER NAME** | **DATA TYPE** |        **DESCRIPTION**         | **DEFAULT** | **VALID VALUES** |
+--------------------+---------------+--------------------------------+-------------+------------------+
| IntfRef **[KEY]**  | string        | Front panel port name          | N/A         | N/A              |
|                    |               | interface id                   |             |                  |
+--------------------+---------------+--------------------------------+-------------+------------------+
| IngressPort        | uint64        | Ingress port buffer stats      | N/A         | N/A              |
+--------------------+---------------+--------------------------------+-------------+------------------+
| PortBufferStat     | uint64        | Per port buffer stats          | N/A         | N/A              |
+--------------------+---------------+--------------------------------+-------------+------------------+
| EgressPort         | uint64        | Egress port buffer stats       | N/A         | N/A              |
+--------------------+---------------+--------------------------------+-------------+------------------+
| IfIndex            | int32         | System assigned interface      | N/A         | N/A              |
|                    |               | id for this port. Read only    |             |                  |
|                    |               | attribute                      |             |                  |
+--------------------+---------------+--------------------------------+-------------+------------------+



*OpxFlexSwitch CURL API Supported*
------------------------------------

	- GET By Key
		 curl -X GET -H 'Content-Type: application/json' --header 'Accept: application/json' -d '{<Model Object as json-Data>}' http://device-management-IP:8080/public/v1/state/BufferPortStat
	- GET ALL
		 curl -X GET http://device-management-IP:8080/public/v1/state/BufferPortStats?CurrentMarker=<x>&Count=<y>
	- GET By ID
		 curl -X GET http://device-management-IP:8080/public/v1/config/BufferPortStatState/<uuid>


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
		response, error = swtch.getBufferPortStatState(IntfRef=intfref)

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
		response, error = swtch.getBufferPortStatStateById(ObjectId=objectid)

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
		response, error = swtch.getAllBufferPortStatStates()

		if error != None: #Error not being None implies there is some problem
			print error
		else :
			print 'Success'


