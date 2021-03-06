---
layout: page
title: "Q194575: PRB: First Item of List Box or Combo Box Not Selectable"
permalink: /kb/194/Q194575/
---

## Q194575: PRB: First Item of List Box or Combo Box Not Selectable

{% raw %}

	Article: Q194575
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You cannot click to select the first item in a list box or combo box when its
	text is wider than the control and its Itemtip is displayed.
	
	RESOLUTION
	==========
	
	Some possible workarounds are:
	
	1. Do not use Itemtips.
	
	2. Make sure the list box or combo box is as wide as the first item in the list.
	  Other items in the list can be longer than the width of the list box or combo
	  box.
	
	3. Click on the first item before the Itemtip appears. The problem only occurs
	  once the Itemtip is displayed.
	
	4. Use the arrow keys on the keyboard to arrow up to the first item.
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Place the following code into a program file and run it:
	
	        *** Beginning of code ***
	        PUBLIC oform1
	        USE HOME(2)+"data\customer"
	        oform1=NEWOBJECT("form1")
	        oform1.Show
	        RETURN
	        *
	        DEFINE CLASS form1 AS form
	             Top = 0
	             Left = 15
	             Height = 289
	             Width = 232
	             DoCreate = .T.
	             Caption = "Form1"
	             Name = "Form1"
	
	             ADD OBJECT list1 AS listbox WITH ;
	                  RowSourceType = 6, ;
	                  RowSource = "customer.company", ;
	                  Height = 169, ;
	                  Left = 24, ;
	                  Top = 24, ;
	                  Width = 84, ;
	                  ItemTips = .T., ;
	                  Name = "List1"
	
	             ADD OBJECT text1 AS textbox WITH ;
	                  Height = 25, ;
	                  Left = 12, ;
	                  Top = 216, ;
	                  Width = 192, ;
	                  Name = "Text1"
	
	             PROCEDURE list1.Click
	                  Thisform.Text1.Value=This.Value
	                  Thisform.Text1.Refresh
	             ENDPROC
	        ENDDEFINE
	        *** End of code ***
	
	2. When running the form, place the mouse pointer over the first item in the
	  list. Once the Itemtip appears, click on it. Note that the text of the item
	  does not appear in the text box below.
	
	3. Place the mouse pointer over any other item in the list until the Itemtip
	  appears. Click on it. Note that it appears in the text box below.
	
	4. Workarounds 3 and 4 in the Resolution section above can be tried while the
	  form is still up. Try clicking on the first item in the list before the
	  Itemtip appears; it will show up in the text box. Select the second or third
	  item in the list, use the arrow keys to move to the first item. Note that it
	  shows up in the text box.
	
	Additional query words: kbVFP600 kbOOP kbCtrl kbContainer
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
