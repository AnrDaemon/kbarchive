---
layout: page
title: "Q105936: FIX: Debugger displays Floating Point Notation for REALs"
permalink: /kb/105/Q105936/
---

## Q105936: FIX: Debugger displays Floating Point Notation for REALs

{% raw %}

	Article: Q105936
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FORTRAN PowerStation for MS-DOS, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The debugger will display real values only in floating point notation in the
	Locals and Watch windows. Other modes of display, such as scientific and
	exponential notations are not available.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in FORTRAN PowerStation version
	1.0. This problem has been resolved with FORTRAN PowerStation maintenance
	release version 1.0a for MS-DOS.
	
	FORTRAN PowerStation version 1.0 can be differentiated from the maintenance
	release version 1.0a by invoking the linker. Typing "link32 | more" (without the
	quotation marks) from \F32\BIN directory will show version 2.8 for FORTRAN
	PowerStation version 1.0, and it will show version 1.0f for the maintenance
	release version 1.0a.
	
	MORE INFORMATION
	================
	
	Many numbers are poorly represented in floating point notation. For instance, a
	very small real value may be displayed as 0.
	
	Sample Code
	-----------
	
	  C Compile options needed: /Zi
	        real*4 x,y
	        x = 1.2345E38
	        y = 1.1234E-38
	        print*, x,y
	        end
	
	In the debugger, step through the program until the print statement. Local and
	watch window on x and y will display:
	
	  X = 123450001585154100000000000000000000000.000000
	  Y = 0.000000
	
	Additional query words: 1.00 IDE
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword3 kbFORTRANPower100DOS
	Version           : :1.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
