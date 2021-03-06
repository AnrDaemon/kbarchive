---
layout: page
title: "Q217057: Unable to Bring New Network Name Resource On Line"
permalink: /kb/217/Q217057/
---

## Q217057: Unable to Bring New Network Name Resource On Line

{% raw %}

	Article: Q217057
	Product(s): Microsoft Windows NT
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbenv kbnetwork kbtool
	Last Modified: 02-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Cluster Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you create a network name resource on a Microsoft Windows NT-based server
	running Windows NT 4.0 Service Pack 4, when you try to bring the resource on
	line, it may fail over to the other node. When this occurs, it may fail between
	both nodes until it goes off line.
	
	CAUSE
	=====
	
	This issue can occur if the "Enable NetBIOS for this IP address" feature is
	disabled for your network name resource. Windows NT 4.0 Service Pack 4 enables
	the "Enable NetBIOS for this IP address" feature, and if this feature is
	disabled, any network name resource that depends on that Internet protocol (IP)
	address does not work when you try to bring it on line. Note that this behavior
	can inadvertently be caused by using the Cluster Administrator tool on a
	computer running Windows NT 4.0 Service Pack 3 to administer a cluster that has
	been updated to Windows NT 4.0 Service Pack 4.
	
	RESOLUTION
	==========
	
	To resolve this issue, verify that the "Enable NetBIOS for this IP address"
	feature is enabled for your network name resource or resources by using the
	version of Cluster Administrator that is included with Windows NT 4.0 Service
	Pack 4.
	
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : kbenv kbnetwork kbtool 
	Technology        : kbAudDeveloper kbClustServSearch
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
