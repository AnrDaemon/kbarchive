---
layout: page
title: "Q150200: FIX: Treeview Control Does Not Receive Key Events"
permalink: /kb/150/Q150200/
---

## Q150200: FIX: Treeview Control Does Not Receive Key Events

{% raw %}

	Article: Q150200
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbVBp400bug kbVBp500fix kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Treeview control does not receive Key events for certain keystrokes. In
	particular, it does not generate events for the Enter key or the arrow
	navigation keys.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 5.0.
	
	MORE INFORMATION
	================
	
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default. Add a
	  TreeView control to Form1. If the TreeView control is not visible in the
	  ToolBox, from the Tools menu, select Custom Controls and select the Microsoft
	  Windows Common Controls. Since TreeView is the only control on Form1, it
	  receives the focus automatically.
	
	2. Place the following code in Form1:
	
	        Private Sub TreeView1_KeyDown(KeyCode As Integer, Shift As Integer)
	
	        Debug.Print "keyDown"
	
	        End Sub
	
	        Private Sub TreeView1_KeyPress(KeyAscii As Integer)
	
	        Debug.Print "keyPress"
	
	        End Sub
	
	        Private Sub TreeView1_KeyUp(KeyCode As Integer, Shift As Integer)
	
	        Debug.Print "keyUp"
	
	        End Sub
	
	3. Run the project by pressing the F5 key. Press the Enter key or an arrow key
	  and notice that no key events are generated. The Escape key, the backspace
	  key, and other keys generate events correctly.
	
	Additional query words: kbVBp400bug kbVBp500fix kbVBp kbdsd kbDSupport kbControl
	
	======================================================================
	Keywords          : kbVBp400bug kbVBp500fix kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
