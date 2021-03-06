---
layout: page
title: "Q171729: HOWTO: Do Generic Callbacks Using a Helper DLL"
permalink: /kb/171/Q171729/
---

## Q171729: HOWTO: Do Generic Callbacks Using a Helper DLL

{% raw %}

	Article: Q171729
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The new AddressOF operator allows you to pass the Address of a Visual Basic
	procedure to a DLL for the purposes of providing a Callback function. However,
	Visual Basic does not let you make the callback directly from within BASIC code.
	This article provides a helper DLL that makes generic callback functionality
	available to BASIC.
	
	MORE INFORMATION
	================
	
	The usual way to use the callback mechanism is to write separate DLL functions
	for each BASIC function prototype. This article details two Visual C++ functions
	that provide a generic callback mechanism for any BASIC function prototype. The
	functions work by manipulating the stack, thus passing the parameters directly
	to the called function.
	
	WARNING: ANY USE BY YOU OF THE CODE PROVIDED IN THIS ARTICLE IS AT YOUR OWN RISK.
	Microsoft provides this code "as is" without warranty of any kind, either
	express or implied, including but not limited to the implied warranties of
	merchantability and/or fitness for a particular purpose.
	
	Visual C++ Code
	---------------
	
	The following code was compiled using Microsoft Visual C++ 4.0 but should work
	with other compilers. This is in a standard DLL project with multi- threaded DLL
	libraries. The calling convention has no prolog code. If you're unsure, have the
	compiler generate an .ASM file, examine the output, and choose a different
	calling convention. You can ignore epilog code because it will never get
	executed.
	
	NOTE: This code is specific to the INTEL platform only.
	
	Callback.DEF
	------------
	
	     LIBRARY   VB5Callback
	
	     EXPORTS
	        Callback
	        Callback2
	
	Callback.CPP
	------------
	
	     __declspec(naked) void Callback()
	     {
	
	     /* For procedures with return values of 8 bytes or less */ 
	     /* Get address to be called and fix-up return address */ 
	
	        _asm  pop   eax;        // save return address
	        _asm  pop   ecx;        // get address to JMP to
	        _asm  push  eax;        // restore return address
	        _asm  jmp   ecx;        // Jump to callback function....
	     }
	
	     __declspec(naked) void Callback2()
	     {
	
	     /* For procedures with return values of more than 8 bytes */ 
	     /* Get address to be called and fix-up return address */ 
	
	        _asm  pop   eax;        // save return address
	        _asm  pop   edx;        // save parameter 0
	        _asm  pop   ecx;        // get address to JMP to
	        _asm  push  edx;        // restore parameter 0
	        _asm  push  eax;        // restore return address
	        _asm  jmp   ecx;        // Jump to callback function....
	     }
	
	Visual Basic Code
	-----------------
	
	The function prototypes in BASIC are achieved by using the DECLARE statement
	because the BASIC compiler does no type checking on the DLL functions. The first
	argument needs to be a LONG with which to pass the address of the function to be
	called. Subsequent arguments and the function return type should match the
	callback function exactly.
	
	Sample Callback Function Declarations:
	--------------------------------------
	
	The callback functions must reside in a standard .BAS module. They cannot reside
	in a Form or Class module:
	
	     Sub Message()
	     Function Calc(ByVal X As Long, Y As Long) As Long
	     Function StrPrt(ByVal S As String) As String
	     Function RetVariant() As Variant
	
	Sample Declare Statements
	-------------------------
	
	The declare statements can be anywhere. If in a Form or Class module, they need
	to be declared using Private Declare ...:
	
	     Declare Sub CallMessage Lib "Callback.dll" Alias "Callback" _
	         (ByVal Addr As Long)
	     Declare Function CallCalc Lib "Callback.dll" Alias "Callback" _
	         (ByVal Addr As Long, ByVal X As Long, Y As Long) As Long
	     Declare Function CallStrPrt Lib "Callback.dll" Alias "Callback" _
	         (ByVal Addr As Long, ByVal S As String) As String
	     Declare Function CallRetVariant Lib "Callback.dll" Alias "Callback2" _
	         (ByVal Addr As Long) As Variant
	
	The use of "Callback" or "Callback2" depends on the function return type as
	explained in the Return Type table (below).
	
	Sample Usage
	------------
	
	The callback functions can be called from anywhere in scope of the prototype
	Declare statement:
	
	     CallMessage AddressOf Message
	     iResult = CallCalc(AddressOf Calc, 6, iNum)
	     S$ = CallStrPrt(AddressOf StrPrt, "The moon is rising over Toledo")
	     Debug.Print CallRetVariant(AddressOf RetVariant)
	
	Return-type Table
	-----------------
	
	The following table indicates which return types should use Callback and which
	should use Callback2 in their Declare statements.
	
	Two versions of the function are required. The first is for Sub routines and all
	Function prototypes whose return type occupies 8 bytes or less, including all
	object types and String. The second is for Function prototypes whose return
	argument is greater than 8 bytes, namely all Variants and those User-Defined
	Types whose length is greater than 8 bytes.
	
	The reason for this dichotomy is that Visual Basic can't return these large data
	types in a register. It passes the address of a pre-allocated structure as an
	implicit parameter on the stack, which the second callback function takes into
	account.
	
	  Return Type                            DLL Function
	  ----------------------------           --------------------
	  All Sub routines                       Callback
	  Byte                                   Callback
	  Integer                                Callback
	  Boolean                                Callback
	  Long                                   Callback
	  Single                                 Callback
	  Double                                 Callback
	  Currency                               Callback
	  Date                                   Callback
	  String                                 Callback
	  Variant                                           Callback2
	  Any object type                        Callback
	  User-defined type (8-bytes or less)    Callback
	  User-defined Type (more than 8 bytes)             Callback2
	
	If you're unsure about which function to use with your user-defined type, you may
	have to try both functions and see which one works. The example below
	illustrates Types requiring both Callback and Callback2:
	
	     Type Size8          ' functions returning this type require Callback
	       A As Long         ' 4 bytes
	       B As String       ' 4-byte pointer - note String discussion below
	     End Type
	
	     Type Size12         ' functions returning this type require Callback2
	       A As Long         ' 4 bytes
	       B As Double       ' 8 bytes
	     End Type
	
	A Note About Strings
	--------------------
	
	Because BASIC is calling a DLL, it will convert string parameters from UNICODE to
	ANSI when calling, and back to UNICODE when returning. If the function returns a
	String, it undergoes the ANSI to UNICODE conversion process also. The callback
	function receives the converted (ANSI) string, which can present problems. This
	also applies to Strings in User-Defined types. There are several ways to deal
	with this problem:
	
	1. Use the StrConv() function in the callback function to do the appropriate
	  conversions upon entry and exit.
	
	2. Use Byte arrays. These don't undergo conversion.
	
	3. Use Variant. These don't undergo conversion and can be used as function
	  return, whereas Byte arrays cannot.
	
	It is recommended that you use a Variant to pass strings as the most simple and
	flexible option.
	
	NOTE: You don't have to use the Callback2 function unless you return a Variant or
	large User-Defined Type as the function result. Using Variants and User-defined
	types as function arguments has no bearing on which DLL function to use in your
	Declare statement.
	
	Other Notes
	-----------
	
	In many cases, you can get similar functionality completely in BASIC by using a
	SELECT CASE statement to call multiple implementations of the same prototype, or
	by using callback objects. The main area where the all-BASIC solution won't
	apply is using components that require calling back into your code and that need
	to call a function rather than an object.
	
	(c) Microsoft Corporation 1997. All Rights Reserved.
	Contributions by Malcolm Stewart, Microsoft Corporation
	
	(c) Microsoft Corporation 1997. All Rights Reserved.
	Contributions by Richard Ault, Microsoft Corporation
	
	
	Additional query words: kbVBp500 kbVBp600 kbVBp kbdsd kbDSupport kbNoKeyWord
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbZNotKeyword3
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
