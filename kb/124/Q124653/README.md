---
layout: page
title: "Q124653: Error Reading WINS Event Detail on a Computer Without WINS"
permalink: /kb/124/Q124653/
---

## Q124653: Error Reading WINS Event Detail on a Computer Without WINS

{% raw %}

	Article: Q124653
	Product(s): Microsoft Windows NT
	Version(s): 3.5 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 4.0 
	- Microsoft Windows NT Server versions 3.5, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to view an event detail generated by the source Windows
	Internet Name Service (WINS) Event Viewer on a system that does not have WINS
	installed, you may the following error message appears:
	
	  The description for Event ID <xxxx> in Source WINS could not be found.
	
	The <xxxx> variable represents the valid Event ID number.
	
	CAUSE
	=====
	
	Event Viewer uses WINSEVNT.DLL provided by the WINS service to map the Event ID
	to a detailed text message. If the WINS service is not installed, Event Viewer
	fails to map the Event ID.
	
	RESOLUTION
	==========
	
	To correct this problem, expand WINSEVNT.DDL_ from the Windows NT Serve version
	3.5 installation media to the %SYSTEMROOT%\SYSTEM32 subdirectory as
	WINSEVNT.DLL.
	
	Additional query words: prodnt log
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS350 kbWinNTS350search
	Version           : 3.5 4.0
	
	=============================================================================
	

{% endraw %}
