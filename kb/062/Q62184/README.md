---
layout: page
title: "Q62184: L2025: &#95;&#95;fltin with Mixed-Language FORTRAN 5.00 and C 6.00"
permalink: /kb/062/Q62184/
---

## Q62184: L2025: &#95;&#95;fltin with Mixed-Language FORTRAN 5.00 and C 6.00

{% raw %}

	Article: Q62184
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a h_fortran | mspl13_c
	Last Modified: 19-JAN-1991
	
	Question:
	
	Why do I get an L2025 multiply-defined symbol error when I link
	together a FORTRAN version 5.00 and a C version 6.00 program? The
	symbol is __fltin.
	
	Sample Code
	-----------
	
	C   FORTRAN MODULE
	      INTERFACE TO SUBROUTINE FOO [C, ALIAS:'_foo'] (N)
	      INTEGER*2 N
	      END
	C   Force a read of a double
	      READ(*,*)DXL
	      CALL FOO (3)
	      END
	
	// C Module
	
	void foo (int x)
	{
	   double j = 3.0 ;
	}
	
	The following are the build options:
	
	   fl /AL /c /FPi fortran.for
	   cl /AL /c /FPi c.c
	   link /nod /noe fortran c, foo.exe,,llibce llibfore ;
	
	The FORTRAN library (llibfore) was created with C compatibility, and
	llibce is a C version 6.00 library.
	
	The linker responds with the following message:
	
	   llibfore.lib(\mrt\c\cfin.ASM) : error L2025: __fltin : symbol
	   defined more than once
	
	   There were 2 errors detected
	
	Under DOS, this does not appear to affect the executable in any way.
	
	Under OS/2, the resulting executable gives SYS0192 when you attempt to
	run it, telling you that there was an error during link time and the
	operating system refuses to run the program.
	
	Microsoft has confirmed this to be a problem with C versions 6.00 and
	6.00a. We are researching this problem and will post new information
	here as it becomes available.

{% endraw %}
