---
layout: page
title: "Q149285: FIX: C1001 When Initialize Array of Type Class with #include"
permalink: /kb/149/Q149285/
---

## Q149285: FIX: C1001 When Initialize Array of Type Class with #include

{% raw %}

	Article: Q149285
	Product(s): Microsoft C Compiler
	Version(s): 4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbVC kbVC500fix
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C/C++ Compiler (CL.EXE), used with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 4.0, 4.1, 4.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you initialize an array of a user-defined type using an include file (see
	the example in this article), the compiler generates this error:
	
	  fatal error C1001: INTERNAL COMPILER ERROR
	  (compiler file 'msc1.cpp', line 899)
	
	RESOLUTION
	==========
	
	There are two workarounds as described below.
	
	- Add a comma after the last element in the include file.
	
	-or-
	
	- Compile the .cpp file with the /P compiler option. This generates a file with
	  a .i extension using the same base name as the .cpp file. Rename the file so
	  that it has a .cpp extension, and compile it, or simply compile the .i file
	  using the /Tp compiler option.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	  .cpp File
	  ---------
	
	     // To reproduce the error, compile options needed: none
	     // Define WORKAROUND to use workaround #1
	
	     struct CMemTblMgr {
	         CMemTblMgr(int);
	         ~CMemTblMgr(void);
	     };
	
	     CMemTblMgr sm_mgrLst[] = {
	     #include "CMEMTABL.INC"
	     };
	
	  Cmemtabl.inc File
	  -----------------
	
	     #ifndef WORKAROUND
	        CMemTblMgr(1),
	        CMemTblMgr(2)
	
	     #else
	        CMemTblMgr(1),
	        CMemTblMgr(2),
	     #endif
	
	Additional query words: kbVC400bug 10.00 10.10 10.20
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbVC kbVC500fix 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : :4.0,4.1,4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
