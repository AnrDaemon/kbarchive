---
layout: page
title: "Q265387: SystemBiosDate Extraction Interprets Date as MM/DD/YY"
permalink: /kb/265/Q265387/
---

## Q265387: SystemBiosDate Extraction Interprets Date as MM/DD/YY

{% raw %}

	Article: Q265387
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a Windows NT 4.0-based computer with a BIOS date that uses a four-digit date
	for the year 2000, Windows NT Diagnostics (Winmsd.exe) truncates the date and
	uses only the first two digits of the year 2000. For example, April 4, 2000, is
	interpreted as 04/04/20 instead of 04/04/2000. The BIOS date information is
	extracted from the following registry location:
	
	  HKEY_LOCAL_MACHINE\HARDWARE\DESCRIPTION\System\SystemBiosDate
	
	CAUSE
	=====
	
	The CmpGetBiosDates function reads dates from the BIOS and populates the
	registry entry each time the computer starts. Windows NT 4.0 assumes that dates
	are in the form of a MM/DD/YY string. However, BIOS manufacturers have expanded
	the date format to MM/DD/CCYY strings. If you run Windows NT 4.0 on a computer
	that has the new BIOS format, the year field is misinterpreted.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time     Size       File name     Platform
	  ----------------------------------------------------
	  06/14/00  01:26pm    954,944  Ntkrnlmp.exe  Intel
	  06/14/00  01:26pm    934,528  Ntoskrnl.exe  Intel
	  06/14/00  01:25pm  1,401,728  Ntkrnlmp.exe  Alpha
	  06/14/00  01:25pm  1,373,632  Ntoskrnl.exe  Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp6 kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTSEnt400SP6a
	Version           : winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
