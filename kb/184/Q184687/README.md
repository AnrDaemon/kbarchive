---
layout: page
title: "Q184687: INFO: Lightweight Controls in Visual Basic 6.0"
permalink: /kb/184/Q184687/
---

## Q184687: INFO: Lightweight Controls in Visual Basic 6.0

{% raw %}

	Article: Q184687
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information about the lightweight, or windowless, controls
	that ship with Visual Basic version 6.0. This article also describes lightweight
	controls, explains their advantages and disadvantages, and illustrates how to
	install lightweight controls in your Visual Basic project.
	
	MORE INFORMATION
	================
	
	Lightweight controls, sometimes referred to as windowless controls, are similar
	to the regular controls shipped in Visual Basic except that they do not have a
	window handle. Because lightweight controls do not have a window handle, these
	controls use less system resources. Lightweight controls are ideal for projects
	where system resources might be a limiting factor, such as Internet applications
	and distributed applications.
	
	Lightweight controls with a Transparent BackStyle property are truly transparent.
	A regular control might appear to be transparent under the same conditions.
	However, the control is still processing Windows messages in that transparent
	background area. When a lightweight control has a transparent background, the
	container holding the lightweight control actually processes the Windows
	messages instead of the lightweight control. Because lightweight controls are
	truly transparent, these controls can be any shape.
	
	There are some disadvantages to lightweight controls. Lightweight control
	containers can only contain other lightweight controls. If you put a regular
	control in a lightweight control container, the container will revert to a
	regular window control container. Regular controls always appear on top of a
	lightweight control because the lightweight control uses the resources of the
	parent window.
	
	When you run Visual Basic, the following controls in your Toolbox are lightweight
	controls:
	
	- Image Control
	- Label Control
	- Line Control
	- Shape Control
	
	In addition to these intrinsic lightweight controls, following are other
	lightweight controls included in the component file MSWLess.ocx that ships with
	Visual Basic 6.0:
	
	- WLCheck Control
	- WLCombo Control
	- WLCommand Control
	- WLFrame Control
	- WLHScroll Control
	- WLVScroll Control
	- WLList Control
	- WLOption Control
	- WLText Control
	
	To use these controls in your Visual Basic program, you must complete the
	following steps:
	
	1. Register the windowless component file in your system registry.
	
	2. Copy the component file and help files to the appropriate directories in your
	  system.
	
	3. Add the ActiveX controls to your Visual Basic program.
	
	How To Register the Windowless Component File
	---------------------------------------------
	
	1. Search for the registration file, MSWLess.reg, on your Visual Basic
	  installation disks. The file is located in the Common\Tools\Vb\WinLess
	  directory on disk 1. NOTE: The windowless controls are in the following
	  location on the August 1998 MSDN CDs: Disk3\Common\Tools\VB\Winless.
	
	2. Double-click MSWLess.reg. The following Registry Editor dialog box appears
	  when you have successfully registered the windowless component file:
	
	  Information in the Common\Tools\Vb\WinLess\MSWLess.reg has been successfully
	  entered into the registry.
	
	You have just registered the windowless component file. The next section shows
	you how to copy the appropriate windowless component and Help files to your
	computer.
	
	How To Copy the Windowless Component Files
	------------------------------------------
	
	1. Search for the following files on your Visual Basic installation disks. These
	  files are located in the Common\Tools\Vb\WinLess directory on disk 1.
	
	  Filename           Description
	  ------------------------------------------------------------------------
	  ltwtct98.chi       Help file on windowless controls.
	  ltwtct98.chm       Help file on windowless controls.
	  MSWLess.ocx        Windowless component file with the windowless ActiveX
	                     Controls.
	
	2. Copy the two Help files to your local Windows\Help directory.
	
	3. Copy the windowless component file, MSWLess.ocx, to your local Windows\System
	  directory.
	
	You have just copied all the necessary windowless component files. The next
	section shows you how to add a windowless control to your Visual Basic program.
	
	How To Add a Windowless Control To Your Project
	-----------------------------------------------
	
	1. Start a new project in Visual Basic.
	
	2. From the Project menu, click Components. The Components dialog box appears.
	
	3. From the Controls tab, select the Microsoft Windowless Controls 6.0 check
	  box.
	
	4. Click OK to close the Components dialog box. All the windowless controls
	  appear on the toolbar.
	
	REFERENCES
	==========
	
	"Creating Lightweight Controls", Visual Basic Product Documentation
	
	For additional information about lightweight controls, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q184645 HOWTO: Create Lightweight Controls with Visual Basic 6.0
	
	For additional installation instructions, please see the following articles in
	the Microsoft Knowledge Base:
	
	  Q189950 HOWTO: Install the Microsoft Windowless Controls for VB6
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q259564 INFO: Windowless Controls in the Mswless.ocx File Are Not Supported
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
