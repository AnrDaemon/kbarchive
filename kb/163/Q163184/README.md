---
layout: page
title: "Q163184: ODE97: Setup Wizard Warning When Including ActiveX Controls"
permalink: /kb/163/Q163184/
---

## Q163184: ODE97: Setup Wizard Warning When Including ActiveX Controls

{% raw %}

	Article: Q163184
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 01-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access 
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	SYMPTOMS
	========
	
	When you use the Microsoft Office 97, Developer Edition Tools to create a custom
	application that includes an ActiveX control and its supporting .dll file(s),
	and you click to select the Run-Time check box on the Database Shortcut
	Properties tab, you may receive the following warning message when the Setup
	program starts to create your disk images:
	
	  File 'C:\Windows\system\ComCat.dll' is also required by a Microsoft
	  Access-provided component. Some properties you have set may be modified.
	
	  If you have not included this file in your Setup program, it may be one
	  of the files needed by an ActiveX control you have added.
	
	CAUSE
	=====
	
	The ODE Setup Wizard will display this message whenever an ActiveX control's
	supporting file, Comcat.dll is added to the Setup program, and you specify that
	the Run-time option be included as well. This behavior occurs because the
	Comcat.dll file is used with the .dep file and the Run- time option.
	
	MORE INFORMATION
	================
	
	When you include the Run-time option, Comcat.dll is automatically included
	behind the scenes but is not added to the Add Files List. When you add an
	ActiveX control (.ocx) file on the Add File page of the ODE Setup Wizard, the
	Setup Wizard searches for the dependency (.dep) file for this control. If it
	finds the .dep file, the Setup Wizard will automatically add the supporting
	file(s) specified in the .dep file to the List Of Files list on the Add Files
	page. Comcat.dll will be included in this list for most of the ActiveX controls
	included in the ODE. So if you are including the Run-time option and an ActiveX
	Control whose .dep file includes Comcat.dll, Comcat.dll is really being included
	twice. This is why you receive the warning message described in the "Symptoms"
	section.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start the ODE Setup wizard.
	
	2. On the Introduction screen click "Create a new set of setup options for my
	  application's custom Setup program."
	
	3. Click Next to move to the next screen which states:
	
	  Add the files that you want your custom Setup program to copy and then set
	  properties for each file.
	
	4. Click Add.
	
	5. Locate the Northwind.mdb database, and then click Add.
	
	6. Click to select the "Set as Application's Main File" check box.
	
	7. Click Add again, and add the file Comdlg32.ocx, to the List Of Files list.
	  Comcat.dll is added automatically.
	
	  NOTE: By default, both files are stored in your Windows/System folder.
	
	8. Click Next to move to the next screen which states:
	
	  Add the shortcuts that you want your custom Setup program to create and then
	  set the properties for each shortcut.
	
	9. Click Add.
	
	10. In the Description box, type a description for your shortcut.
	
	11. On the Database Shortcut Properties tab, click to select the Run-time check
	  box.
	
	12. Click Next until you get to the screen which states:
	
	  Where do you want the Setup Wizard to copy the files for your custom Setup
	  program.
	
	13. Click to select the "Network or CD Setup" check box, and then click Finish.
	
	  Note that when the ODE Setup Wizard starts creating the disk images, you
	  receive the message mentioned in the "Symptoms" section.
	
	REFERENCES
	==========
	
	For more information about .ocx files and their supporting .dll files, search
	the Microsoft ODE Setup Wizard Help Index for "supporting files for ActiveX
	controls."
	
	Additional query words: file c windows system comcat dll is also required by a Microsoft Access-provided component
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbOfficeSearch kbAudDeveloper kbAccessSearch kbOffice97Search kbOffice97 kbOffice97DevSearch
	Version           : WINDOWS:
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
