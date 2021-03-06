---
layout: page
title: "Q86748: Windows: Virtual Printer Memory Defined"
permalink: /kb/086/Q86748/
---

## Q86748: Windows: Virtual Printer Memory Defined

{% raw %}

	Article: Q86748
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The term "virtual memory" when used in connection with PostScript printers
	actually refers to a portion of the physical RAM installed in the printer. This
	type of printer memory is separate and distinct from the RAM memory on the
	computer or the free disk space on the computer's hard disk that Windows 386
	enhanced mode uses as its own type of virtual memory.
	
	The following sections discuss the definition and description of printer virtual
	memory, virtual memory settings in the Printers section of the Control Panel,
	and sources of information about printer virtual memory.
	
	MORE INFORMATION
	================
	
	Description of Printer Virtual Memory
	-------------------------------------
	
	The phrase "virtual memory" used in the context of PostScript printing describes
	the way that the PostScript language uses certain segments of the printer's RAM
	memory.
	
	The PostScript usage of memory can be divided into two basic areas. The first
	area is the area that is reserved for PostScript operations. This area includes
	the PostScript interpreter and three of its stacks: the operand stack, the
	dictionary stack, and the execution stack. The second area of memory, the
	virtual memory, or VM, area, is the area in which the values for PostScript
	composite objects are stored. PostScript objects are simply data, such as
	numbers, booleans, strings, and arrays. A composite object may be an array,
	dictionary, or string.
	
	The interpreter and its stacks manipulate objects and composite objects during
	the PostScript printing process. Therefore, the first area of memory may be
	thought of as corrected overhead for operations. The second area of memory is
	storage area for data that is dynamically adjustable through the Advanced
	Options dialog box for PostScript printers (see below).
	
	Virtual Memory Settings in Control Panel
	----------------------------------------
	
	After you install a PostScript printer driver in Windows 3.1, the Advanced button
	will be available in the Options dialog box. (To access the Options dialog box,
	run Control Panel, choose the Printers icon, choose the Setup button, and choose
	the Options button.) If you choose the Advanced button, you will enter the
	Advanced Options dialog box, which has a Memory group box in which you can set
	the amount of PostScript printer virtual memory. The desired amount is entered
	in the Virtual Memory (KB) box.
	
	The default setting that appears in the Virtual Memory box is the one recommended
	by the printer manufacturer. The default value is adequate in most cases.
	However, when a document uses a large number of TrueType or soft fonts, it may
	be useful to reduce the virtual memory setting so that the printer's memory is
	cleared more often. This helps to prevent the printer's memory from being
	overloaded with unused font information.
	
	The Clear Memory Per Page option performs a similar function. With this option,
	the printer's memory is cleared after each page is printed, and the fonts are
	downloaded to the printer again. However, these settings have only limited
	effectiveness in dealing with PostScript printing problems.
	
	You can determine the actual amount of RAM memory (that is, "virtual memory") on
	a PostScript printer by printing the TESTPS.TXT file in the WINDOWS directory.
	Adding more physical RAM to the printer will allow you to increase the maximum
	effective value in the Virtual Memory box.
	
	Sources of Documentation
	------------------------
	
	Although page 334 of the "Microsoft Windows Resource Kit" guide for operating
	system version 3.1 implies that more details exist concerning virtual printer
	memory in chapter 4 ("Troubleshooting") of the "Getting Started with Microsoft
	Windows" guide, no additional information specific to printer virtual memory
	exists there. Nonetheless, the "To change a PostScript printer's options"
	section on page 84 of the "Getting Started with Microsoft Windows" guide does
	provide information about the Clear Memory Per Page check box. Other information
	about virtual memory is found by choosing the Help button or by pressing F1
	while the insertion point is in the Virtual Memory settings box.
	
	REFERENCES
	==========
	
	"PostScript Language Reference Manual," Adobe Systems Inc., pages 18-19, 45-46,
	Addison-Wesley, 1990
	
	"Microsoft Windows Resource Kit" for Windows version 3.1, page 334
	
	"Getting Started with Microsoft Windows," version 3.1, page 84
	
	HELP.TXT, Windows version 3.1
	
	
	Additional query words: vertial vertual random access memory printing fonts post-script post script
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
