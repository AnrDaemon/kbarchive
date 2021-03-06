---
layout: page
title: "Q253821: System Error 85 with &quot;NET USE&quot; Command"
permalink: /kb/253/Q253821/
---

## Q253821: System Error 85 with &quot;NET USE&quot; Command

{% raw %}

	Article: Q253821
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): kbenv kberrmsg
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, 4.0 SP5, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When a non-administrative user attempts to reconnect to a shared network drive
	that the user has already used, system error 85 ("Local device name already in
	use") may be generated.
	
	For example, running the following sequence of commands in a logon script or from
	a command prompt illustrates the issue:
	
	  net use r: /d
	  net use r: \\<servername>\<share>
	  net use r: /d
	  net use r: \\<servername>\<share>
	
	The behavior does not occur for users with administrative privileges.
	
	CAUSE
	=====
	
	This behavior is caused by a setting of 1 in the following registry value:
	
	  HKLM\System\CurrentControlSet\Control\SessionManager\ProtectionMode
	
	If the setting is 1, the problem occurs. If you change the setting to 0 and
	reboot the server, the problem disappears.
	
	Note that the following articles in the Microsoft Knowledge Base suggest changing
	this value to 1 to restrict changes to Base System objects and for solving
	problems with symbolic links:
	
	  Q218473 Restricting Changes to Base System Objects
	
	  Q244995 Base System Object Restrictions Are Not Enabled by Default
	
	  Q222159 Symbolic Link Case Sensitivity Exploit Bypasses System Security
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Change the entry for
	
	  HKLM\System\CurrentControlSet\Control\SessionManager\ProtectionMode
	
	from 1 to 0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServ400sp4 kbNTTermServ400sp5 kbNTTermServSearch
	Version           : winnt:4.0,4.0 SP4,4.0 SP5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
