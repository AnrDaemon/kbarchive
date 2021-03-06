---
layout: page
title: "Q191503: FIX: Unexpected Results Display With Input Mask"
permalink: /kb/191/Q191503/
---

## Q191503: FIX: Unexpected Results Display With Input Mask

{% raw %}

	Article: Q191503
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When typing a new value, such as 5.25, into a blank text box that has an input
	mask similar to 999,999.99, an extra zero is added between the decimal and the
	last digit entered before the decimal.
	
	CAUSE
	=====
	
	This problem occurs when an input mask contains one or more commas and the
	number of digits entered before the decimal does not fill out the number of
	places to the left of the commas.
	
	RESOLUTION
	==========
	
	This problem only occurs in Visual FoxPro 5.x. Visual FoxPro 3.x and 6.0 do not
	exhibit this problem. Therefore, upgrading to Visual FoxPro 6.0 is a possible
	resolution.
	
	Here are two possible resolutions you can use for Visual FoxPro 5.x:
	
	- Do not use an input mask with numeric data. If the ControlSource of the text
	  box is a numeric field in a table, you will not be able to enter alphabetic
	  data into the text box, with or without an input mask. The drawback to this
	  method is that commas will not show when you enter large numbers.
	
	- Instead of a Numeric type field in the table, use a Double type field. Then
	  use the K format code in the Format property of the text box along with the
	  input mask.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	
	MORE INFORMATION
	================
	
	The InputMask property of fields and controls restricts or dictates the format
	of user input. In Visual FoxPro 5.x, if a text box has a numeric field in a
	table as a ControlSource and the InputMask property of the text box is set to
	999,999.99, entering a number with three or less digits to the left of the
	decimal causes an additional zero to remain immediately to the left of the
	decimal point. Entering numbers with four or more digits to the left of the
	decimal point do not cause the problem with the extra zero.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Enter the following code into a program file and save the program:
	
	        PUBLIC oform1
	        CREATE TABLE xjunkpr FREE (f1 N(10,2))
	        oform1=CREATEOBJECT("form1")
	        oform1.Show
	        RETURN
	
	        **************************************************
	        *-- Form:         form1
	        *-- ParentClass:  form
	        *-- BaseClass:    form
	        *
	        DEFINE CLASS form1 AS form
	
	           Top = 0
	           Left = 0
	           DoCreate = .T.
	           Caption = "Form1"
	           Name = "Form1"
	
	        ADD OBJECT command1 AS commandbutton WITH ;
	           Top = 168, ;
	           Left = 240, ;
	           Height = 73, ;
	           Width = 121, ;
	           Caption = "Quit", ;
	           TabIndex = 5, ;
	           Name = "Command1"
	
	        ADD OBJECT command2 AS commandbutton WITH ;
	           Top = 24, ;
	           Left = 240, ;
	           Height = 73, ;
	           Width = 121, ;
	           Caption = "New Record", ;
	           TabIndex = 1, ;
	           Name = "Command2"
	
	        ADD OBJECT text1 AS textbox WITH ;
	           ControlSource = "xjunkpr.f1", ;
	           Format = "", ;
	           Height = 25, ;
	           InputMask = "999,999.99", ;
	           Left = 24, ;
	           TabIndex = 2, ;
	           Top = 24, ;
	           Width = 168, ;
	           Name = "Text1"
	
	        ADD OBJECT command3 AS commandbutton WITH ;
	           Top = 168, ;
	           Left = 24, ;
	           Height = 49, ;
	           Width = 73, ;
	           Caption = "Prior", ;
	           TabIndex = 4, ;
	           Name = "Command3"
	
	        ADD OBJECT command4 AS commandbutton WITH ;
	           Top = 168, ;
	           Left = 120, ;
	           Height = 49, ;
	           Width = 73, ;
	           Caption = "Next", ;
	           TabIndex = 3, ;
	           Name = "Command4"
	
	        PROCEDURE command1.Click
	           Thisform.Release
	        ENDPROC
	
	        PROCEDURE command2.Click
	           APPEND BLANK
	           Thisform.Refresh
	        ENDPROC
	
	        PROCEDURE command3.Click
	           SKIP -1
	           IF BOF()
	              GO TOP
	           ENDIF
	           Thisform.Refresh
	        ENDPROC
	
	        PROCEDURE command4.Click
	           SKIP 1
	           IF EOF()
	              GO BOTTOM
	           ENDIF
	           Thisform.Refresh
	        ENDPROC
	
	        ENDDEFINE
	        *
	        *-- EndDefine: form1
	        **************************************************
	
	2. Run the program.
	
	3. Click (or press ENTER) the New Record button to add a new record to the
	  table.
	
	4. Press Tab once to move the cursor to the text box.
	
	5. Enter a number with a decimal point, for example, enter "5.25" (without the
	  quotes).
	
	6. Note that once the first digit it entered, 0.00 appears at the right end of
	  the text box. Then when the decimal is entered, the digit and leading zero
	  remain and the insertion point moves to the right of the decimal.
	
	Additional query words: kbVFp600fix kbOOP kbvfp500
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINDOWS:5.0,5.0a
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
