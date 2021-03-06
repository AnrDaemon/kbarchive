---
layout: page
title: "Q216108: Memory Leak and STOP Screens Using Intermediate NDIS Drivers"
permalink: /kb/216/Q216108/
---

## Q216108: Memory Leak and STOP Screens Using Intermediate NDIS Drivers

{% raw %}

	Article: Q216108
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): _IK
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When intermediate (layered) NDIS miniport drivers are in use on Windows NT
	Server 4.0, Terminal Server Edition, you may experience one or both of the
	following:
	
	- A memory leak in kernel nonpaged pool memory. Over time, memory may be
	  depleted to the point where system stability is compromised.
	
	- You may receive the following blue-screen STOP error message with parameters
	  that indicate the bad instruction is in the Ndis.sys driver:
	
	  STOP: 0x0000000A (0x00000014, 0x00000002, 0x00000000, 0xFCBA1062)
	  IRQL_NOT_LESS_OR_EQUAL (* Address fcba1062 has base at fcb95000 - NDIS.SYS)
	
	CAUSE
	=====
	
	Intermediate drivers are typically add-ons that layer themselves over hardware
	drivers as a filter to provide additional functionality, such as data encryption
	or other value-added services. The Ndis.sys driver included in Windows NT 4.0
	has been found to have some deficiencies when such intermediate drivers are
	used.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT Server 4.0, Terminal
	Server Edition. This problem was first corrected in Windows NT Server 4.0,
	Terminal Server Edition Service Pack 4.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          : _IK 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
