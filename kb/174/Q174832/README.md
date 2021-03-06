---
layout: page
title: "Q174832: DOC: Incorrect Internet Transfer Control GetChunk Example"
permalink: /kb/174/Q174832/
---

## Q174832: DOC: Incorrect Internet Transfer Control GetChunk Example

{% raw %}

	Article: Q174832
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kberrmsg kbdocerr kbVBp500
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Running the GetChunk example code from the Visual Basic 5.0 Help file generates
	a run-time error:
	
	  '35764' - still executing last request.
	
	Instead of intercepting icResponseReceived notification in the StateChanged event
	as shown in the Help file for Internet Transfer Control GetChunk method, the
	correct code should intercept icResponseCompleted notification.
	
	MORE INFORMATION
	================
	
	The following example shows the correct way to use Transfer Control GetChunk
	method.
	
	Step-by-Step Example
	--------------------
	
	1. Start Visual Basic 5.0. If you are already running Visual Basic, choose New
	  Project on the File menu. Create a Standard EXE project. Form1 is created by
	  default.
	
	2. Add a CommandButton, Command1, to Form1.
	
	3. Add an Internet Transfer Control, Inet1, to Form1.
	
	4. Add the following code to the Code window:
	
	        Private Sub Command1_Click()
	            Inet1.Execute "http://www.microsoft.com", "GET"
	            'download the start page of microsoft.com
	        End Sub
	
	        Private Sub Inet1_StateChanged(ByVal State As Integer)
	           ' Retrieve server response using the GetChunk
	           ' method when State = 12. This example assumes the
	           ' data is text.
	
	           Select Case State
	           ' ... Other cases not shown.
	
	           Case icResponseCompleted ' 12
	              Dim vtData As Variant ' Data variable.
	              Dim strData As String: strData = ""
	              Dim bDone As Boolean: bDone = False
	
	              ' Get first chunk.
	              vtData = Inet1.GetChunk(1024, icString)
	
	              Do While Not bDone
	
	                 strData = strData & vtData
	                 ' Get next chunk.
	                 vtData = Inet1.GetChunk(1024, icString)
	                 If Len(vtData) = 0 Then
	                    bDone = True
	                 End If
	              Loop
	
	              MsgBox strData
	           End Select
	
	        End Sub
	
	Additional query words: msinet.ocx
	
	======================================================================
	Keywords          : kberrmsg kbdocerr kbVBp500 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500
	Version           : WINDOWS:5.0
	
	=============================================================================
	

{% endraw %}
