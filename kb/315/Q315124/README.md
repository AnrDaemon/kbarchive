---
layout: page
title: "Q315124: SAMPLE: Use the Winsock ActiveX Control with Visual FoxPro"
permalink: /kb/315/Q315124/
---

## Q315124: SAMPLE: Use the Winsock ActiveX Control with Visual FoxPro

{% raw %}

	Article: Q315124
	Product(s): Microsoft FoxPro
	Version(s): 6.0,7.0
	Operating System(s): 
	Keyword(s): kbfile kbActiveX kbInternet kbGrpDSFox kbDSupport
	Last Modified: 15-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 6.0, 7.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The FoxSock.exe sample is adapted from the first Microsoft Visual Basic sample
	presented in the article "Using the Winsock Control", which is available at the
	following MSDN Web site:
	
	  http://msdn.Microsoft.com/library/default.asp?url=/library/en-us/vbcon98/html/vbconusingwinsockcontrol.asp
	
	The Microsoft Winsock Control ships with Visual FoxPro (VFP) 6.0 and 7.0. It is
	not supported in VFP 5.0. This sample has been tested on Microsoft Windows 98,
	Microsoft Windows 2000, and Microsoft Windows XP.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  FoxSock.exe
	  (http://download.microsoft.com/download/visualfoxpro7/sample/1.0/NT5XP/EN-US/FoxSock.exe)
	
	Release Date: February 22, 2002
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	The FoxSock.exe file contains the following files:
	
	+--------------------+
	| File name   | Size | 
	+--------------------+
	| Summary.txt | 2K   | 
	+--------------------+
	| Winsock.pjx | 2K   | 
	+--------------------+
	| Winsock.pjt | 4K   | 
	+--------------------+
	| Winsock.prg | 1K   | 
	+--------------------+
	| Server.scx  | 3K   | 
	+--------------------+
	| Server.sct  | 7K   | 
	+--------------------+
	| Client.scx  | 3K   | 
	+--------------------+
	| Client.sct  | 7K   | 
	+--------------------+
	
	To use this sample, follow these steps:
	
	1. Unzip FoxSock.exe to your computer, and then set the default directory in
	  Visual FoxPro to the directory to which you extracted the files.
	
	2. Run Winsock.prg to launch the server and client forms.
	
	3. Click Connect on the client form, and type some text in the Send text box in
	  either form. When you leave the Send box, your text will appear in the other
	  form's Receive box.
	
	Differences from the Visual Basic sample include the following:
	
	- You need to use the ".Object" syntax when you call the Winsock control's
	  methods (for instance, oleWinsock.Object.Connect) instead of referring to the
	  control directly from the OleControl.
	
	- The control setup code is placed in the Init method instead of the Load
	  method. The Visual Basic example does not close the connection. If you close
	  the forms in VFP without closing the connection first, VFP appears to stop
	  responding (hang) for a while.
	
	- Additional settings (Close buttons, tab order) were made for clarity.
	
	Additional query words: FoxSock
	
	======================================================================
	Keywords          : kbfile kbActiveX kbInternet kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600 kbVFP700
	Version           : :6.0,7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
