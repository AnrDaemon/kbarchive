---
layout: page
title: "Q115283: Installing Sound Producer Pro Alters ANSI Escape Sequences"
permalink: /kb/115/Q115283/
---

## Q115283: Installing Sound Producer Pro Alters ANSI Escape Sequences

{% raw %}

	Article: Q115283
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.x,6.0,6.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Prompts, menus, screen colors, or screen settings that use ANSI escape sequences
	do not function properly after you install the Orchid Sound Producer Pro
	software.
	
	CAUSE
	=====
	
	When making modifications to the CONFIG.SYS and/or AUTOEXEC.BAT file(s), the
	setup program for the Orchid Sound Producer Pro software converts all the
	letters in these files to uppercase. This may alter the functionality of certain
	entries that use ANSI escape sequences.
	
	RESOLUTION
	==========
	
	To correct this problem, manually edit the AUTOEXEC.BAT and/or CONFIG.SYS
	file(s) and change letters in all statements that use an ANSI escape sequence
	(such as PROMPT, ECHO, and so forth) back to the proper case.
	
	STATUS
	======
	
	Orchid Technical Support has confirmed that this is a problem in versions 1.0
	and 1.1 of the Sound Producer Pro software. For more information, contact Orchid
	Technical Support.
	
	MORE INFORMATION
	================
	
	As an example, the following MS-DOS PROMPT command results in bright red text on
	a black background:
	
	  prompt $e[1m$e[31m$e[40m $p$g
	
	If this line is converted to uppercase letters as follows
	
	  PROMPT $E[1M$E[31M $E[40M $P$G
	
	the result is white text on a black background, and the prompt appears as
	follows:
	
	  MMM C:\>
	
	The Orchid Sound Producer Pro is manufactured by Orchid Technology, a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	this product's performance or reliability.
	
	Additional query words: 5.00 6.00 6.20 color all caps case sensitive sensitivity
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.x,6.0,6.2
	
	=============================================================================
	

{% endraw %}
