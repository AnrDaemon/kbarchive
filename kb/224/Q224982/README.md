---
layout: page
title: "Q224982: Err: STOP 0x0000001e {0xc000005, 0xa1000aa7, 0x0, 0x00440194}"
permalink: /kb/224/Q224982/
---

## Q224982: Err: STOP 0x0000001e {0xc000005, 0xa1000aa7, 0x0, 0x00440194}

{% raw %}

	Article: Q224982
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP4
	Operating System(s): 
	Keyword(s): kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP4 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the value of the process ID (PID) of any given process exceeds 65,535 or
	0x10000, Win32k.sys generates the following error message on a blue screen:
	
	  STOP 0x0000001e {0xc000005, 0xa1000aa7, 0x00000000, 0x00440194}
	
	NOTE: The first parameter will always be 0xc0000005 and the second parameter will
	always fall within the memory range of Win32k.sys.
	
	CAUSE
	=====
	
	When a process terminates, Win32k.sys must release structures allocated by that
	process. Win32k.sys tracks these structures by PID number. The driver Win32k.sys
	only supports PID numbers within the 0-65,535 range (ushort).
	
	This problem occurs because a program is not releasing thread handles. When a
	thread is created, a handle is allocated out of the system handle table as well
	as the process handle table. This system handle table is the same handle table
	process IDs come from. This can cause the value of the process ID numbers to
	exceed 65,535 or 0x10000.
	
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT Server version 4.0, Terminal Server Edition Service Pack 6.
	
	MORE INFORMATION
	================
	
	After you install the hotfix, if you attempt to create a process with an ID
	value greater than 65,535, the following pop-up error message is displayed and
	the process create does not work:
	
	  Initialization of the dynamic link library USER32.DLL failed. The process is
	  terminating abnormally.
	
	To find the process that is not releasing thread handles, use Performance Monitor
	to find a process with a high handle count.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp4 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp4 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0,4.0 SP4
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
