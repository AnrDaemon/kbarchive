---
layout: page
title: "Q161209: PRB: Resizing OCX Does Not Resize Its Component Control(s)"
permalink: /kb/161/Q161209/
---

## Q161209: PRB: Resizing OCX Does Not Resize Its Component Control(s)

{% raw %}

	Article: Q161209
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When resizing your ActiveX control on a host form, the component controls or
	user-drawn graphics do not get resized.
	
	CAUSE
	=====
	
	You do not have logic in the Resize event of the UserControl object to resize
	the component control(s) to the new size, or in the Paint event of the
	UserControl object to redraw the user-drawn graphics.
	
	RESOLUTION
	==========
	
	Add code to the UserControl's Resize and/or paint event to resize the component
	control(s) and user-drawn graphics.
	
	STATUS
	======
	
	This is behavior is by design.
	
	MORE INFORMATION
	================
	
	Even though you may want to have various effects when the developer resizes your
	ActiveX control, Visual Basic has no way of determining how to handle resize
	issues of your component controls. You can place code in the UserControl_Resize
	event to handle the resizing in whatever manner you wish.
	
	If your control has no component controls, the UserControl_Paint event allows you
	to redraw the user-drawn graphics.
	
	Several examples are included below. All code is in the UserControl object.
	
	Resizing a Single Control
	-------------------------
	
	The control is resized to fill the entire UserControl by using the following
	code:
	
	        Private Sub UserControl_Resize()
	          Text1.Move 0, 0 , ScaleWidth, ScaleHeight
	        End Sub
	
	Resizing a Control and a Label Side-by-Side
	-------------------------------------------
	
	The label occupies the leftmost 20% of the user control. The textbox occupies the
	rightmost 75% of the user control. A 5% gap exists between them, as shown here:
	
	        Private Sub UserControl_Resize()
	          Label1.Move 0, 0 , ScaleWidth * .2, ScaleHeight
	          Text1.Move ScaleWidth * .25, 0, ScaleWidth * .75, ScaleHeight
	        End Sub
	
	Resizing a Shape Control with a Label Drawn Part-Way Down
	---------------------------------------------------------
	
	The shape control fills the entire UserControl. The label occupies the full width
	and is drawn slightly above center as shown here:
	
	        Private Sub UserControl_Resize()
	          Shape1.Move 0, 0 , ScaleWidth, ScaleHeight
	          Label1.Move 0, (ScaleHeight - Label1.Height) * .4, ScaleWidth
	        End Sub
	
	The height of the label is assumed not to change in this example. To change label
	height to be 30% of the UserControl height, add the 4th argument to the Move
	method:
	
	        Label1.Move 0, ScaleHeight * .28, ScaleWidth, ScaleHeight * .3
	
	The change of the second argument to ScaleHeight * .28 is obtained by
	substituting ScaleHeight * .3 for Label1.Height, giving:
	
	        (ScaleHeight - ScaleHeight * .3) * .4
	        (ScaleHeight * .7) * .4
	        ScaleHeight * .28
	
	Resizing User-Drawn Graphics
	----------------------------
	
	The code draws a border around the UserControl and puts an 'X' in it. The
	ScaleMode needs to be in pixels for the border to paint correctly:
	
	        Private Sub UserControl_Paint()
	          UserControl.ScaleMode = vbPixels
	          UserControl.Line (0, 0)-(ScaleWidth - 1, ScaleHeight - 1), 0, B
	          UserControl.Line (0, 0)-(ScaleWidth - 1, ScaleHeight - 1), 0
	          UserControl.Line (0, ScaleHeight - 1)-(ScaleWidth - 1, 0), 0
	        End Sub
	
	REFERENCES
	==========
	
	Microsoft Visual Basic User's Guide, Chapter 4, Creating an ActiveX Control,
	Drawing the ShapeLabel Control
	
	Additional query words: kbVBp500 kbVBp600 kbdse kbDSupport kbVBp kbvbcc kbActiveX
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbZNotKeyword3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
