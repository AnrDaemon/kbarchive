---
layout: page
title: "Q114228: HOWTO: Add Icons After Distributed Setup Program Is Run"
permalink: /kb/114/Q114228/
---

## Q114228: HOWTO: Add Icons After Distributed Setup Program Is Run

{% raw %}

	Article: Q114228
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5x,2.6,2.6a,3.0,5.0
	Operating System(s): 
	Keyword(s): kbcode kbinterop kbvfp300 kbvfp500
	Last Modified: 09-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6, 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	More icons can be added to your application group after the Setup program is run
	for a distributed application created with the FoxPro for Windows Distribution
	Kit. You can add these icons by using dynamic data exchange (DDE) to send
	commands to the Windows Program Manager.
	
	MORE INFORMATION
	================
	
	After running the Setup program for your distributed application, users may want
	to add other icons and program groups for help or README files. By using DDE to
	send commands to the Windows Program Manager, you can create a new program group
	or add items to existing program groups.
	
	The following example shows how to initiate a DDE channel to the Windows Program
	Manager, create a program group called "My Application", and add an item with a
	particular icon (in this case the Help icon that comes with FoxPro).
	
	     iChannel = DDEInitiate("Progman","Progman")
	     = DDEExecute(iChannel,;
	      "[Additem(c:\myapp\readme.txt,tty,;
	      c:\foxprow\goodies\bitmaps\fox\help.ico,0)]")
	     = DDETerminate(iChannel)
	
	This program can then be compiled into an .EXE file. At the end of the Setup
	program, you can tell your users to run this .EXE file after installing the
	application.
	
	REFERENCES
	==========
	
	Microsoft Windows Software Development Kit (SDK) "Programmer's Reference Volume
	1: Overview," version 3.1, Chapter 17.2, "Command-String Interface"
	
	FoxPro for Windows "Developer's Guide," version 2.5, Chapter 12, "Dynamic Data
	Exchange (DDE)"
	
	FoxPro Distribution Kit for Windows "User's Guide," version 2.5, Chapter 4,
	"Creating Distribution Disks"
	
	Additional query words: Distribution Kit icon DK Setup
	
	======================================================================
	Keywords          : kbcode kbinterop kbvfp300 kbvfp500 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro260 kbFoxPro260a kbVFP300 kbVFP500
	Version           : WINDOWS:2.5x,2.6,2.6a,3.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
