---
layout: page
title: "Q192549: INFO: Overview of Debugging VBCE Applications"
permalink: /kb/192/Q192549/
---

## Q192549: INFO: Overview of Debugging VBCE Applications

{% raw %}

	Article: Q192549
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbDebug kbToolkit kbVBp500 kbVBp600 kbOSWinCE100 kbGrpDSVB
	Last Modified: 16-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes some of the resources available for debugging
	applications created with the Microsoft Windows CE Toolkit for Visual Basic
	(VBCE).
	
	MORE INFORMATION
	================
	
	A VBCE program is handled differently by the integrated development environment
	(IDE) than a regular Visual Basic application. VBCE programs are completely
	compiled into .pvb files before they are handed off to pvb.exe, which actually
	runs the code in the program. VBCE programs run completely outside of the Visual
	Basic IDE, so there is no compile on demand as in regular Visual Basic. Only
	very basic syntax checking is done by the add-in (CEIDE.DLL) when the program is
	compiled; therefore, some errors will not be caught until run-time.
	
	Debugger
	--------
	
	VBCE comes with a separate Debugger utility (VBDBG.EXE) for debugging Windows CE
	applications. The Debugger runs as a separate program outside of the Visual
	Basic IDE, therefore some of the debugging options available in the Visual Basic
	IDE are not supported by the toolkit.
	
	The Debugger includes several useful windows: A Watch Window displays the values
	of variables or expressions during execution. An Immediate Window allows small
	code statements to run. A Call Stack shows procedures in execution. An Object
	window shows the hierarchy of running objects. Objects can be opened to view
	their code, add breakpoints, etc. Applications are compiled before reaching the
	debugger, so application code cannot be edited in the debugger's Immediate
	Window. Because all errors, other than syntax errors, are caught at run-time,
	applications must be running in either the emulated or remote Windows CE
	environment before you can begin the debugging process. Though most debugging is
	done while in emulation mode, you should also debug your application on the
	remote device in order to ensure your application is error-free.
	
	Breakpoints entered in the Visual Basic IDE will not be recognized in the
	Debugger, but breakpoints can be added in the Debugger's code window for the
	object.
	
	Error Trapping
	--------------
	
	The "On Error Resume Next" statement is useful when performing inline error
	handling. This statement is the only error handling statement the toolkit
	currently supports. On Error Resume Next does not clear the Err object, so you
	can use inline error handling to display a meaningful error messages rather than
	displaying the generic "Application Error" message.
	
	Although VBCE programs keep running after generating an application error,
	execution of the current procedure halts unless an On Error Resume Next
	statement is in the procedure and before where the error occurred.
	
	The Debug object is not supported in VBCE. Alternative strategies could be using
	the File control to log information about program execution or using MsgBoxes
	and controls to display program status.
	
	The "On Error GoTo 0" line is included in VBCE to disable inline error handling.
	If you use this line in code, subsequent errors may cause executing code to
	stop, although the rest of the application will continue.
	
	Err Object
	----------
	
	Run-time errors produce a generic Application Error dialog box with the message:
	
	  An error was encountered while running this program.
	
	There is no other information about what may have caused the error, and no Help
	button to retrieve information from the online Help files. When an application
	error occurs, the Err object is loaded with the error number and a description
	of the error.
	
	You can check the Err object in your code in various ways, including displaying
	the error information in a MsgBox, such as:
	
	  MsgBox <Err.Number> vbCrLf <Err.Description>
	
	If the error is coming from a control, the Err.Source property can be checked.
	Usually, the Err object supplies enough information to determine what caused the
	error. Tracing through a program with the debugger can reveal more information.
	After code is modified, recompile the .pvb to test your changes. If a program is
	still running on the device or emulator, it must be closed before trying to run
	it again from the IDE.
	
	REFERENCES
	==========
	
	Windows CE Toolkit Help for Visual Basic 6.0
	
	Additional query words: wince wce tshooting debug trap vbce vbce6
	
	======================================================================
	Keywords          : kbDebug kbToolkit kbVBp500 kbVBp600 kbOSWinCE100 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbWinCETKVBSearch kbWinCESearch kbWinCETK100VB600
	Version           : :1.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
