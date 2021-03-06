---
layout: page
title: "Q138008: PCMCIA Utilities for Windows NT"
permalink: /kb/138/Q138008/
---

## Q138008: PCMCIA Utilities for Windows NT

{% raw %}

	Article: Q138008
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	PCMCMD.EXE and PCMCIA are two separate utilities that can be used to
	troubleshoot a PCMCIA (PC Card) problem.
	
	MORE INFORMATION
	================
	
	PCMCMD.EXE is located on the Windows NT Workstation and Server CD-ROM disks
	under the \SUPPORT\DEBUG\<platform> directory. The PCMCIA applet is
	included with the Windows NT 3.51 Resource Kit.
	
	PCMCMD.EXE
	----------
	
	This utility reads the tuple (hardware configuration) information of the card and
	dumps the information. You may run the program from Windows NT command prompt,
	by typing:
	
	  PCMCMD > PCCARD.TXT
	
	PCCARD.TXT now contains text information such as the manufacturer, product name,
	and product information. If PCMCMD doesn't dump any information, the Windows NT
	enabler probably cannot detect the PC CARD.
	
	PCMCIA Applet
	-------------
	
	After you install the Windows NT 3.51 Resource Kit, the Windows NT Control Panel
	contains the PCMCIA applet. The applet, similar to PCMCMD utility, provides
	information about the PC CARD device currently installed on the system.
	
	Additional query words: PCCARD PC-CARD prodnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	
	=============================================================================
	

{% endraw %}
