---
layout: page
title: "Q261251: XCON: Check DNS When Receiving Event ID 9318 with Error 1722"
permalink: /kb/261/Q261251/
---

## Q261251: XCON: Check DNS When Receiving Event ID 9318 with Error 1722

{% raw %}

	Article: Q261251
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 28-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In the versions of Microsoft Exchange Server listed at the beginning of this
	article, you may experience some or all of the following symptoms:
	
	- Mail backs up between one of the servers in a site and all of the other
	  servers in the site.
	
	- Numerous instances of the following warning event may be logged:
	
	  Event ID: 9318
	  Source: MSExchangeMTA
	  Type: Warning
	  Category: Interface Description
	  An RPC communications error occurred.
	  Unable to bind over RPC. The locality table (LTAB) index is 76.
	  Windows NT error code: 1722. [BASE IL MAIN BASE 1 500] (12)
	
	- If you ping by IP, the ping is successful.
	
	- If you ping by server name, the ping may be successful at times and
	  unsuccessful at other times.
	
	- RPC ping does not work in one direction. It works from the answering server,
	  but it does not work from the calling server to the answering server.
	
	- If you restart the server, you temporarily resolve the issue. However, after
	  a period of time, mail flow stops again on the server.
	
	CAUSE
	=====
	
	This behavior can occur if there are two Domain Name System (DNS) servers
	selected in the TCP/IP stack on the server, and the second DNS server points to
	a server that is still on the network, but which is no longer being used for DNS
	purposes. When, because of network problems, the server selects the secondary
	DNS setting, name resolution no longer occurs and connectivity is lost.
	
	RESOLUTION
	==========
	
	To resolve this issue, follow these steps:
	
	1. Right-click Network Neighborhood on the desktop, and then select Properties.
	
	2. Click the Protocols tab, select TCP/IP Protocol, and then click Properties.
	
	3. Click the DNS tab, and then in the "DNS Service Search Order "box, verify
	  whether the IP addresses for the DNS servers listed are accurate. If an
	  address is incorrect, click the Edit button to change the incorrect address
	  to the correct address. If the address is valid but the server is no longer
	  being used for DNS, click the Remove button to delete the entry.
	
	WORKAROUND
	==========
	
	To work around this issue, restart the server to force the DNS information to
	read into memory from the first DNS server in the list. This strategy is a
	temporary workaround until the next network failure.
	
	MORE INFORMATION
	================
	
	For additional information about Event 9318, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q170056 XCON: Messages Back Up on MTA with Event 9215 and Event 9318
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
