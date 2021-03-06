---
layout: page
title: "Q139076: BUG: Mpw2lib Fails on Long File Names"
permalink: /kb/139/Q139076/
---

## Q139076: BUG: Mpw2lib Fails on Long File Names

{% raw %}

	Article: Q139076
	Product(s): Microsoft C Compiler
	Version(s): MACINTOSH:2.0
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, Macintosh Cross-Development Addon, version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When converting MPW-formatted object files for file names longer than the
	standard 8.3 MS-DOS format, Mwp2lib may generate an application error similar to
	one of these:
	
	  The instruction at xxxx referenced memory at xxxx. The memory could not be
	  written.
	
	  -or-
	
	  The instruction at xxxx referenced memory at xxxx. The memory could not be
	  read.
	
	CAUSE
	=====
	
	Mpw2lib cannot handle an object file that has a file name longer than the
	standard 8.3 MS-DOS format.
	
	RESOLUTION
	==========
	
	Truncate the object file name to eight characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Mpw2lib is a Windows utility used to convert MPW (Macintosh Programmer's
	Workbench) formatted object files to COFF (Common Object File Format) library
	files. The resulting file can be linked with code generated by Visual C++ for
	Macintosh. The file is transferred from the Macintosh to the Windows system
	using the Mfile utility. Windows NT allows you to preserve the long file names
	of the Macintosh in most cases.
	
	You may not receive the error message for long file names. The problem appears to
	be inconsistent and can appear more frequently with longer file names.
	Occasionally, you may generate the following error instead of the previously
	listed error messages:
	
	  Fatal error M2L1003: Can't open file "xxx.o"
	
	In general, however, it is safe to stay with long file names.
	
	
	REFERENCES
	==========
	
	68K Programmer's Guide, Appendix E: MFILE Technical Reference
	68K Programmer's Guide, Appendix F: MPW2LIB Technical Reference
	
	Additional query words: 2.00 dskbsweep
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVCsearch kbHWMAC kbOSMAC kbAudDeveloper kbVCXDev200Mac
	Version           : MACINTOSH:2.0
	
	=============================================================================
	

{% endraw %}
