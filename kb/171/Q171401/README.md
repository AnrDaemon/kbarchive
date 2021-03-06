---
layout: page
title: "Q171401: Routing and Remote Access Event 1003"
permalink: /kb/171/Q171401/
---

## Q171401: Routing and Remote Access Event 1003

{% raw %}

	Article: Q171401
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your computer running both Windows NT Server and the Routing and Remote Access
	Service (RRAS) does not start and you may experience one or more of the
	following problems:
	
	- When you try to start the Routing and Remote Access service from Services in
	  Control Panel you receive the following error message:
	
	  Services
	  The Routing and Remote Access Service service returned service specific error
	  1003.
	
	  -or-
	
	- The event viewer may log the following event message:
	
	  Event ID: 7024
	  Source: Service Control Manager
	  Description: The Routing and Remote Access Service service returned service
	  specific error 1003.
	
	  -or-
	
	- When you attempt to start the router in Routing and Remote Access Admin, the
	  service stops responding.
	
	CAUSE
	=====
	
	A system component, such as a protocol or service, that is used by Routing and
	Remote Access has been installed after applying Service Pack 3.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, use the following steps:
	
	1. Reinstall Service Pack 3.
	
	2. When you are prompted to replace newer files, click No to All.
	
	3. Restart the computer when prompted.
	
	4. Update Routing and Remote Access Service
	
	  a. Click Start, point to Settings, and click Control Panel.
	
	  b. Double click the Network icon.
	
	  c. Choose the Services tab.
	
	  d. Select Routing and Remote Access Service.
	
	  e. Click Update.
	
	  f. Specify the installation location, the default is
	
	     C:\program files\routing
	
	  g. When prompted to reboot, click Yes
	
	MORE INFORMATION
	================
	
	When adding a protocol or component, the files are installed from the Windows NT
	4.0 compact disc. This replaces the files that were installed from Service Pack
	3.
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
