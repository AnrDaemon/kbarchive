---
layout: page
title: "Q163662: Running Multiple Instances of an Application Causes STOP x50"
permalink: /kb/163/Q163662/
---

## Q163662: Running Multiple Instances of an Application Causes STOP x50

{% raw %}

	Article: Q163662
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 25-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Running several instances of an application on a multiprocessor computer may
	cause Windows NT to stop responding (hang) while displaying the following error
	message on a blue screen:
	
	  STOP 0x00000050
	
	
	CAUSE
	=====
	
	In rare circumstances and only on multiple processor computers, the printer
	driver is unloaded.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
