---
layout: page
title: "Q218619: Taskpads Let Web Sites Invoke Executables on a User's Computer"
permalink: /kb/218/Q218619/
---

## Q218619: Taskpads Let Web Sites Invoke Executables on a User's Computer

{% raw %}

	Article: Q218619
	Product(s): Microsoft Windows NT
	Version(s): WINDOWS:; winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 98 
	- Microsoft BackOffice Server 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Taskpads is a feature that allows users to view and run Windows management tools
	through an HTML page rather than the Windows control. A vulnerability has been
	discovered in Taskpads that lets Web sites invoke executables on a user's
	workstation.
	
	CAUSE
	=====
	
	This vulnerability results because certain methods provided by Taskpads are
	incorrectly marked as "safe for scripting."
	
	RESOLUTION
	==========
	
	A patch is available for this issue that removes the Taskpads functionality,
	which is rarely used.
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression tested and should be applied only to systems
	determined to be at risk of attack. Please evaluate your system's physical
	accessibility, network and Internet connectivity, and other factors to determine
	the degree of risk to your system. If your system is sufficiently at risk,
	Microsoft recommends you apply this fix.
	
	To resolve this problem immediately, obtain the fix as described below. For a
	complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Windows 98 Resource Kit and Windows 98 Resource Kit Sampler
	-----------------------------------------------------------
	
	This patch has been posted to the following Internet location:
	
	  ftp://ftp.microsoft.com/reskit/win98/taskpads/
	
	BackOffice Resource Kit, Second Edition
	---------------------------------------
	
	This patch has been posted to the following Internet locations:
	
	  x86:
	  ftp://ftp.microsoft.com/reskit/nt4/x86/taskpads/
	
	  Alpha:
	  ftp://ftp.microsoft.com/reskit/nt4/alpha/taskpads/
	
	STATUS
	======
	
	Microsoft has confirmed this problem could result in some degree of security
	vulnerability in Taskpads included with the Windows 98 Resource Kit, the Windows
	98 Resource Kit Sampler, and the BackOffice Resource Kit, second edition.
	
	MORE INFORMATION
	================
	
	Taskpads is included with:
	
	- Microsoft Windows 98 Resource Kit
	
	- Microsoft Windows 98 Resource Kit Sampler (included as part of Windows 98 but
	  not installed by default)
	
	- Microsoft BackOffice Resource Kit, second edition
	
	Additional query words: 4.00 98 95 rkit reskit ms99-007 Patch Available for TaskPad Scripting Vulnerability
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin98search kbBackOfficeSearch kbWin98 kbBackOfficeServ400
	Version           : WINDOWS:; winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
