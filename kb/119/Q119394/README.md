---
layout: page
title: "Q119394: PRB: Using References with va_&#42; Macros from stdarg.h"
permalink: /kb/119/Q119394/
---

## Q119394: PRB: Using References with va_&#42; Macros from stdarg.h

{% raw %}

	Article: Q119394
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,2.0,2.1,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCRT kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600
	Last Modified: 11-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), included with:
	   - Microsoft C/C++ for MS-DOS 
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 4.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft C++, if you use functions that accept a variable number of
	arguments, you may encounter problems when trying to use the va_* family of
	functions to access the parameters if the second parameter used for the va_start
	macro is a reference type.
	
	CAUSE
	=====
	
	This problem is caused by the way that the va_start macro is defined and the way
	that the C++ language handles taking the address of a reference. Applying the
	"address of" operator to a reference type results in a pointer to the object
	that is being referred to. The va_start macro takes the address of the last
	named parameter to locate subsequent parameters. When the last named parameter
	is a reference, this causes problems because the macro is no longer referring to
	the current call stack but whatever follows the object being referred to, which
	could be a previous call stack or a global memory object.
	
	RESOLUTION
	==========
	
	The workaround is to redefine the va_start macro to use inline assembly to
	subvert the C++ language.
	
	NOTE: This solution is not portable and will require changing if you intend your
	source code to be used on non-Intel platforms.
	
	MORE INFORMATION
	================
	
	The va_start macro is used in conjunction with the va_arg macro to "walk" the
	stack to get the parameters passed to the variable argument list. The va_start
	macro is defined as follows:
	
	     #define va_start(ap,v)  ( ap = (va_list)&v + _INTSIZEOF(v) )
	
	where va_list is defined as a char * on Intel platforms. The macro parameter "ap"
	is of type va_list. The problem arises from taking the address of the second
	parameter, "v", if v is a reference type. The net result of this macro being
	expanded is that ap is supposed to point to the first of the variable
	parameters. Casting v to a non-reference type intuitively seems like the logical
	solution, but because the result of a cast is not an l-value, the compiler
	returns an error message.
	
	NOTE: The only way to get an l-value from a cast is to cast the value to a
	reference type, which results in the same problem.
	
	Sample Code
	-----------
	
	The sample code below demonstrates a solution for this problem:
	
	  /* Compile options needed:  none
	  */ 
	
	  #include <stdio.h>
	  #include <stdarg.h>
	
	  // Uncomment the following lines to work-around the problem:
	  // 
	  // #ifdef va_start
	  // #undef va_start
	  // 
	  // #ifdef _WIN32
	  // #define va_start(ap,v) {int var= _INTSIZEOF(v); \ 
	  //                __asm lea eax,v __asm add eax,var __asm mov ap,eax \ 
	  //                }
	  // #else
	  // #define va_start(ap,v) { int var=_INTSIZEOF(v);\ 
	  //                __asm lea ax,v __asm add ax,var __asm mov ap,ax\ 
	  //                }
	  // #endif
	  // #endif
	
	  void numprint( int &first ... )
	  {
	    va_list ap;
	
	    va_start( ap, first );
	    printf("%d\n", first );
	    int ival = va_arg( ap, int );
	    printf("%d\n", ival );
	    double dval = va_arg( ap, double );
	    printf( "%.2f\n", dval );
	    va_end(ap);
	  }
	
	  void main()
	  {
	    int i=100,j=1000;
	    float f=999.99;
	
	    numprint( i,j,f );
	  }
	
	Additional query words: ellipsis
	
	======================================================================
	Keywords          : kbCRT kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : :1.0,1.5,2.0,2.1,4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
