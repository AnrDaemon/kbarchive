---
layout: page
title: "Q260247: XFOR: Message Looping with Exchange Server on a Windows 2000 DC"
permalink: /kb/260/Q260247/
---

## Q260247: XFOR: Message Looping with Exchange Server on a Windows 2000 DC

{% raw %}

	Article: Q260247
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If Exchange Server 5.5 is installed on a Microsoft Windows 2000 domain
	controller, some Internet e-mail messages may loop if the following conditions
	are met:
	
	- The Windows 2000 domain is <domain>.com.
	
	- The Exchange Server Simple Mail Transfer Protocol (SMTP) site address is
	  <exchangedomain>.com.
	
	- The domain <domain>.com does not have an MX record configured in DNS.
	
	- Exchange Server is configured to reroute all e-mail messages except e-mail
	  messages to <exchangedomain>.com (set to deliver inbound).
	
	- A message is sent to <domain>.com.
	
	The following events may be logged in the application event log:
	
	  
	
	- Event ID: 4115
	  Event Type: Error
	  Event Source: MSExchangeIMC
	  Event Category: Internal Processing
	
	  Description:
	  The message from the spool file <archivename> seems to be looping
	  through the routing extension for the Internet Mail Service. Please check
	  that the routing DLL is configured properly.
	
	- Event ID: 12071
	  Event Type: Warning
	  Event Source: MSExchangeIS
	  Event Category: Content Engine
	
	  Description:
	  Message <MessageID> with subject <subject of message> from
	  <sender> exceeded the maximum hop count(80040C02-8200008C). The archive
	  filename is <archivename>.
	
	- Event ID: 4098
	  Event Type: Error
	  Event Source: MSExchangeIMC
	  Event Category: Internal Processing
	
	  Description:
	  The following message could not be delivered because the hop count exceeded
	  the maximum. Check your configuration to make sure messages are not looping.
	  From: <sender>
	  Subject: <subject of message>
	
	CAUSE
	=====
	
	This behavior occurs because Internet Mail Service is connecting to itself in an
	attempt to deliver the message.
	
	It is important to note that this is not a problem with either Exchange Server or
	Windows 2000. Refer to the "More Information" section of this article for
	further explanation of this behavior.
	
	RESOLUTION
	==========
	
	To resolve this problem, use one of the following methods:
	
	- Add an MX record for <domain>.com in DNS specifying the proper mail
	  host.
	
	- Add <domain>.com in the "Specify by E-Mail Domain" area on the
	  Connections tab of Internet Mail Service properties specifying the proper
	  mail host.
	
	- On the Routing tab of Internet Mail Service, configure <domain>.com to
	  route to the correct destination mail host.
	
	NOTE: The first two methods are the best ways to resolve this issue. Although the
	third method prevents the message from looping, it still causes Internet Mail
	Service to first connect to itself to deliver the message and then reroutes the
	message to its intended destination.
	
	MORE INFORMATION
	================
	
	When a Windows 2000 domain controller is created, it registers an A record for
	its Windows 2000 domain. In the situation described in this article, the Windows
	2000 domain is <domain>.com.
	
	NOTE: This domain should not be confused with the domain used for Internet mail.
	The domain <domain>.com specifies a security namespace, while the domain
	<exchangedomain>.com specifies a messaging namespace. The two namespaces
	are completely separate, and can have different names. Therefore an A record for
	<domain>.com is dynamically registered in DNS, and it points to the IP
	address of the domain controller.
	
	When Internet Mail Service tries to deliver an SMTP message, the service first
	queries DNS for an MX record for the destination domain. If the query does not
	return an MX record for the destination domain, Internet Mail Service queries
	DNS for an A record for the destination domain. If an A record is returned,
	Internet Mail Service connects to the IP address specified in the A record and
	delivers the message.
	
	In this situation, Internet Mail Service attempts to deliver the message to
	itself because of the following reasons:
	
	- The MX record query does not return any records because an MX record is not
	  configured in DNS.
	
	- The A record query successfully finds the A record for the domain controller.
	
	
	Additional query words: XMRP imc
	
	======================================================================
	Keywords          : kberrmsg kbnetwork exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
