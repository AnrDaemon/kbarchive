---
layout: page
title: "Q27297: Passing BASIC User-Defined Type to C by Near Reference"
permalink: /kb/027/Q27297/
---

## Q27297: Passing BASIC User-Defined Type to C by Near Reference

{% raw %}

	Article: Q27297
	Product(s): See article
	Version(s): 4.00 4.00b 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | B_BasicCom S_C S_QuickC | mspl13_basic
	Last Modified: 6-NOV-1989
	
	The example below demonstrates how to pass a user-defined type from
	compiled BASIC to Microsoft C by near reference.
	
	This information about inter-language calling applies to QuickBASIC
	Versions 4.00, 4.00b, and 4.50 for MS-DOS and to Microsoft BASIC
	Compiler Versions 6.00 and 6.00b for MS-DOS and MS OS/2.
	
	For more information about passing other types of parameters between
	BASIC and C, and a list of which BASIC and C versions are compatible
	with each other, query in the Software/Data Library on the following
	word:
	
	   BAS2C
	
	Code Example
	------------
	
	REM ===== BASIC PROGRAM =====
	
	TYPE record
	   a AS INTEGER
	   b AS STRING * 20
	   c AS SINGLE
	END TYPE
	
	DECLARE SUB TypeReference CDECL (SEG p1 AS record)
	
	CLS
	DIM element AS record
	element.a = 128
	element.b = DATE$ + CHR$(0)
	element.c = 39.6
	CALL TypeReference(element)
	END
	
	/* ===== C ROUTINE ===== /*
	
	#include <stdio.h>
	struct record{
	       int a;
	       char b[20];
	       float c;
	       };
	
	void TypeReference(element)
	     struct record near *element;
	 {
	     printf("Record.A = %d\n",element->a);
	     printf("Record.B = %s\n",element->b);
	     printf("Record.C = %f\n",element->c);
	 }
	
	===== OUTPUT =====
	
	Record.A = 128
	Record.B = 02-02-1988
	Record.C = 39.599998

{% endraw %}
