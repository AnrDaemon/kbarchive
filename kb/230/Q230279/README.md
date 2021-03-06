---
layout: page
title: "Q230279: Corrupted User Profiles Can Cause New Local Default to Be Lost"
permalink: /kb/230/Q230279/
---

## Q230279: Corrupted User Profiles Can Cause New Local Default to Be Lost

{% raw %}

	Article: Q230279
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP4
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 SP4, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you download a corrupted profile from the central server, error 1009 is
	logged in the Event System log. A new local profile is then created from the
	local default setting. However, after you restart your computer, the computer
	does not reference the new local profile and begins the cycle of loading the
	corrupted profile from the server again. The following error message is then
	displayed:
	
	  The system cannot find the drive specified.
	
	CAUSE
	=====
	
	This problem occurs when Terminal Server detects a certain type of profile
	corruption. A flag is set, causing the reference to the newly created user
	profile to not be saved in the registry. The user is given a new copy of the
	local default profile and can make changes to it. These changes are saved to the
	hard disk. When the computer is restarted, it searches for the local version to
	check the time stamp versus the server version. This check is ONLY made against
	profiles listed in the registry (not against the physical files in the profile
	directory) and thus, the recently created local copy is ignored. The computer
	then repeats the process of downloading the server copy (which is still
	corrupted) and the cycle repeats.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0. This problem was
	first corrected in Windows NT Server 4.0, Terminal Server Edition, Service Pack
	5.
	
	MORE INFORMATION
	================
	
	For more information about this problem in Windows NT, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q216867 Corrupted User Profiles Can Cause New Local Default to be Lost
	
	Additional query words: wts tse
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400sp4 kbNTTermServSearch
	Version           : winnt:4.0 SP4
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
