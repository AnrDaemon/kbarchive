---
layout: page
title: "Q110255: Performance Drops During Large File Copy"
permalink: /kb/110/Q110255/
---

## Q110255: Performance Drops During Large File Copy

{% raw %}

	Article: Q110255
	Product(s): Microsoft Windows NT
	Version(s): 3.1,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.1, 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	System performance drops to an unacceptable level while a large file is being
	copied.
	
	CAUSE
	=====
	
	This problem may be a symptom of a problem with the way that the Server service
	interacts with the system cache in certain configurations.
	
	RESOLUTION
	==========
	
	You may be able to work around this problem by tuning the server to prevent the
	providing of large amount of memory to the system cache.
	
	To do this, perform the following steps:
	
	1. Start Control Panel Network.
	
	2. From the Installed Network Software box, select Server, and then click
	  Configure.
	
	3. If the option "Maximize Throughput for File Sharing" is currently selected,
	  you may get better performance during large file copy operations by selecting
	  the "Maximize Throughput for Network Applications" or "Balance" options.
	
	4. If you elected to make a change in Step 3, restart your computer so the
	  change can take effect.
	
	MORE INFORMATION
	================
	
	The "Maximize Throughput for File Sharing" option permits the system cache to
	use more available memory than it would otherwise. In this situation, the
	available memory can drop to levels that result in heavy swapping activity on
	the hard disks in order to accommodate requests from user or system applications
	that may subsequently need to be swapped into memory.
	
	The cache manager periodically gives up memory that it has allocated so that the
	system will never run completely out of memory due to caching alone. This can
	happen whenever a file copy operation is complete or when a threshold value is
	reached. This means that the problem described above does not occur if a series
	of smaller files are copied. The threshold value, when "Maximize Throughput for
	File Sharing" option is not selected, is enough higher than the threshold value
	when the problem does not occur there either.
	
	This problem is also more noticeable on computers with lower total physical
	memory. When more total physical memory is available, the minimum available
	memory threshold is also higher, which can alleviate the problem.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT and Windows NT
	Advanced Server version 3.1. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodnt 3.10
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : :3.1,3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
