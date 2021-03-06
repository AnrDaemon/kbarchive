---
layout: page
title: "Q252186: Stop 0x0000000A in RDR.SYS Removing Dormant Server Connections"
permalink: /kb/252/Q252186/
---

## Q252186: Stop 0x0000000A in RDR.SYS Removing Dormant Server Connections

{% raw %}

	Article: Q252186
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv kbWinNT4sp6fixkbfixlist
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When your Windows NT Terminal Server-based computer removes dormant server
	connections, it may generate an error message similar to the following error
	message in the Rdr.sys file on a blue screen:
	
	  STOP: 0x0000000A (0xf7223c1c, 0x00000002, 0x00000000, 0xf71e9ec5)
	  IRQL_NOT_LESS_OR_EQUAL
	
	NOTE: The parameters may differ based on your computer configuration, but the
	last parameter (0xf71e9ec5) will be the same if you are running the x86 version
	of Windows NT, Terminal Server Edition with Service Pack 5 installed.
	
	CAUSE
	=====
	
	This problem can occur when the redirector tries to obtain access to a timeout
	value that is stored in paged pool memory while running at Dispatch Level.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	version 4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	This problem was first corrected in Windows NT Server version 4.0, Terminal
	Server Edition Service Pack 6.
	
	MORE INFORMATION
	================
	
	The following is an example of the information you may receive if you use the
	Kernel Debugger tool to view a memory dump:
	
	NOTE: Some of the numeric information may differ based on your computer
	configuration, however, the symbolic information will be similar if not exactly
	the same.
	
	0: kd> !Trap bfbc7e94
	!Trap bfbc7e94
	eax=00000000 ebx=f71ede10 ecx=001b997a edx=82297d70 esi=f71edd90
	edi=f71edf08 eip=f71e9ec5 esp=bfbc7f08 ebp=bfbc7f18 iopl=0
	nv up ei ng nz na pe cy
	vip=0 vif=0
	cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000
	efl=00010283
	ErrCode = 00000000
	f71e9ec5 030d1c3c22f7 add ecx,[rdr!RdrFailedConnectTimeout
	(f7223c1c)]
	0: kd> !k
	!k
	ChildEBP RetAddr
	bfbc7f18 f71ee186 rdr!RdrScavengeServerEntries+0x2f
	bfbc7f20 f71eb4d7 rdr!RdrTimer+0x6
	bfbc7f34 8010c1cd rdr!RdrExecutiveWorkerThreadRoutine+0x41
	bfbc7f4c 8014056c ntkrnlmp!ExpWorkerThread+0x73
	bfbc7f7c 8014c0be ntkrnlmp!PspSystemThreadStartup+0x54
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbWinNT4sp6fix kbfixlist
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
