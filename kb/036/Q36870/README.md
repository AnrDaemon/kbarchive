---
layout: page
title: "Q36870: INFO: C2106 Error Assigning a String Literal to a char Array"
permalink: /kb/036/Q36870/
---

## Q36870: INFO: C2106 Error Assigning a String Literal to a char Array

{% raw %}

	Article: Q36870
	Product(s): Microsoft Programming Utilities
	Version(s): 1.0,1.5,6.0,6.0a,6.0ax; MS-DOS:7.0; winnt:1.0,2.0,2.1,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kberrmsg kbLangC kbVC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600
	Last Modified: 15-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C for MS-DOS, versions 6.0, 6.0a, 6.0ax 
	- Microsoft C/C++ for MS-DOS, version 7.0 
	- Microsoft Visual C++, version 1.5 
	- Microsoft Visual C++, versions 1.0, 2.0, 2.1, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A common programming error in C involves an attempt to fill a character array,
	declared as "char arrayname[somelength]," with a string constant by using the
	simple-assignment operator (the equal sign, "="). This attempt fails and the
	compiler generates the following message:
	
	  error C2106: '=' : left operand must be lvalue
	
	Simple assignment works to fill non-auto (global) character arrays and character
	pointers (in C version 5.0 and later) with static text. The required
	declarations are as follows:
	
	     char string1[10] = "String1";
	     char *string2 = "String2";
	
	The text below presents two code examples to demonstrate correct and incorrect
	methods to initialize strings.
	
	MORE INFORMATION
	================
	
	The following code example does not compile correctly and produces the C2106
	error.
	
	Sample Code
	-----------
	
	  /*
	   * Compile options needed: None
	   */ 
	
	  #include <string.h>
	  char string1[10];
	
	  void main(void);
	  void main(void)
	  {
	     string1 = "String1";
	  }
	
	The following example demonstrates various methods to copy strings.
	
	Sample Code
	-----------
	
	  /*
	   * Compile options needed: None
	   */ 
	
	  /* This example demonstrates some string usage principles. */ 
	  #include <stdio.h>
	  #include <string.h>
	  #include <malloc.h>
	
	  char string1[40];       /* string1 is an array of char  */ 
	  char *string2;          /* string2 is a pointer to char */ 
	          /* Important: Know when to malloc space for string2. */ 
	
	  void main(void);
	  void main(void)
	  {
	     /* This shows the correct way to achieve the   */ 
	     /* assignment intended by string1 = "String1"; */ 
	     strcpy(string1, "Contents of string1");
	     printf("1:%s\n\n", string1);
	
	     /* These two assignments show two ways to     */ 
	     /* use a char pointer with a string literal.  */ 
	     string2 = "Contents of string2"; /* point to the literal */ 
	     printf("2:%s\n", string2);
	
	     /* allocate memory for char *string2 to point at */ 
	     string2 = (char *)malloc(sizeof(string1));
	     strcpy(string2, "Contents of string2, again");
	     printf("3:%s\n\n", string2);
	     free(string2);
	
	     /* This shows a failed attempt to fill a char  */ 
	     /* array by assignment through a char pointer. */ 
	     string2 = string1;
	     string2 = "Contents of string2, but not string1";
	     printf("4:%s\n", string1);
	     printf("5:%s\n\n", string2);
	
	     /* This shows how correctly to use a pointer   */ 
	     /* to fill a char array with a string literal. */ 
	     string2 = string1;
	     strcpy(string2, "Contents of string2, and also string1");
	     printf("6:%s\n", string1);
	     printf("7:%s\n\n", string2);
	  }
	
	This code generates the following output:
	
	  1:Contents of string1
	
	  2:Contents of string2
	
	  3:Contents of string2, again
	
	  4:Contents of string1
	  5:Contents of string2, but not string1
	
	  6:Contents of string2, and also string1
	  7:Contents of string2, and also string1
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbLangC kbVC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbZNotKeyword8 kbvc150 kbvc100 kbCCompSearch kbZNotKeyword3 kbCComp600DOS kbCComp600aDOS kbCComp600axDOS kbCVC700DOS kbVC500 kbVC600 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : :1.0,1.5,6.0,6.0a,6.0ax; MS-DOS:7.0; winnt:1.0,2.0,2.1,4.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
