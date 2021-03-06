---
layout: page
title: "Q34985: PRB: A2102 Warnings Generated for Possible 80286 Problems"
permalink: /kb/034/Q34985/
---

## Q34985: PRB: A2102 Warnings Generated for Possible 80286 Problems

{% raw %}

	Article: Q34985
	Product(s): Microsoft Macro Assembler
	Version(s): 5.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), version 5.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Macro Assembler (MASM) versions 5.1 and 5.1a will generate a
	warning for the following sample code, while MASM version 6.0, 6.0a, and 6.0b
	will assemble it without error. The warning generated by 5.1 and 5.1a is as
	follows
	
	  A4102: segment near (or at) 64K limit
	
	The linkers that shipped with both products (versions 3.64 and 5.13,
	respectively) will report the following error at link time
	
	  L4020: code-segment size exceeds 64K-36
	
	CAUSE
	=====
	
	Warnings are generated because code segments in the range of 65,501 - 65,536
	bytes may be unreliable on certain 80286 processors.
	
	MORE INFORMATION
	================
	
	The size of a 16-bit segment is limited to 64K. The recommendation of having
	segments no larger than 65,500 (64K-36) is to avoid problems with certain 80286
	processors.
	
	When the segment really does exceed 64K, MASM 5.1 and 5.1a generate an error
	rather than a warning
	
	  A2102: segment near (or at) 64K limit
	
	and MASM 6.0, 6.0a, 6.0b generates an error as well
	
	  A2103: segment exceeds 64K limit
	
	The following sample code will cause MASM to generate warnings, since the segment
	size is between 65,501 and 65,536 bytes. Increasing the size of 'value' to
	65,550 will result in errors rather than warnings.
	
	Sample Code
	-----------
	
	  ; Assemble options needed: none
	
	  .model small,c
	  .286
	
	  .stack
	  .code
	
	  start:
	
	      MOV ax, @data
	      MOV ds, ax
	
	      value db 65500 dup ( ? )
	
	      MOV ah, 4ch
	      INT 21h
	
	      END start
	
	Additional query words: 5.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510
	Version           : :5.1
	
	=============================================================================
	

{% endraw %}
