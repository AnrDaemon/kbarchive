---
layout: page
title: "Q169716: XCON: Exchange MTA Generates Event ID 37"
permalink: /kb/169/Q169716/
---

## Q169716: XCON: Exchange MTA Generates Event ID 37

{% raw %}

	Article: Q169716
	Product(s): Microsoft Exchange
	Version(s): WinNT:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server message transfer agent (MTA) may fail to deliver
	messages between servers that are connected via a schedulable connector (such as
	X.400 or Dynamic RAS), and in turn generate the following Event Ids in the
	Application Event Log:
	
	  MSExchangeMTA Event ID: 37
	  Type: Warning
	  Category: Security
	  The
	  /O=OrganizationName/OU=SiteName/CN=Configuration/CN=Connections/CN=Conne
	  ct orName (Adjacent-MTA) entity attempted to open an association while
	  suspended. [MTA XFER-IN 22 35] (14)
	
	  MSExchangeMTA Event ID: 1293
	  Type: Warning
	  Category: X.400 Service
	  A remotely-initiated association from
	  /O=OrganizationName/OU=SiteName/CN=Configuration/CN=Connections
	  /CN=ConnectorName was refused. The failure reason provider is 0 and the
	  reason is 0. Control block index 1. Type 1. [PLATFORM KERNEL 26 128]
	  (12)
	
	CAUSE
	=====
	
	If the Event ID 37 is generated, it is an indication that a schedulable
	connector on the Exchange Server computer that logged the event is currently
	configured for a connection schedule of "Never," which indicates that the
	connector will neither accept nor initiate a connection to another Exchange
	Server computer. Therefore, when another MTA attempts to make a connection to
	this Exchange Server computer, it is refused because the current schedule set
	for this connector is configured as "Never." The Exchange Server computer
	attempting to initiate the connection with the Exchange Server computer where
	the connector is currently configured for a connection schedule of "Never" will
	typically log one or more of the following events upon failure of the attempted
	connection:
	
	  MSExchangeMTA Event ID: 1290
	  Type: Warning
	  Category: X.400 Service
	  A locally initiated association to
	  /O=OrganizationName/OU=SiteName/CN=Configuration/CN=Connections
	  /CN=ConnectorName was refused. The failure reason provider was 0 and the
	  reason was 0. Control block index 202. Type 1. [PLATFORM KERNEL 20 130]
	  (12)
	
	  MSExchangeMTA Event ID: 289
	  Type: Warning
	  Category: X.400 Service
	  A connection to
	  /O=OrganizationName/OU=SiteName/CN=Configuration/CN=Connections/CN=Conne
	  ctorName could not be opened. [MTA XFER-IN 17 26] (12)
	
	  MSExchangeMTA Event ID: 1294
	  Type: Warning
	  Category: X.400 Service
	  An association with entity
	  /O=OrganizationName/OU=SiteName/CN=Configuration
	  /CN=Connections/CN=ConnectorName ended abnormally. [198 1 0 1 PLATFORM
	  KERNEL 20 130] (10)
	
	WORKAROUND
	==========
	
	In order for the MTAs to communicate successfully via a configured connector,
	each connector involved must be configured for a connection schedule other than
	"Never". The Schedule tab on the connector's property page provides control over
	when the connector is available.
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WinNT:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
