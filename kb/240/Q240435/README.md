---
layout: page
title: "Q240435: PATCH: WCELoad.exe Fixes ActiveX Hanging Problem on Palm-size PC"
permalink: /kb/240/Q240435/
---

## Q240435: PATCH: WCELoad.exe Fixes ActiveX Hanging Problem on Palm-size PC

{% raw %}

	Article: Q240435
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0,2.11,3.0
	Operating System(s): 
	Keyword(s): kbfile kbpatch kbAppSetup kbDeployment kbToolkit kbVBp600 kbGrpDSVB kbOSWinCE211 kbDSup
	Last Modified: 26-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0, version 1.0 
	- Microsoft Windows CE version 2.11 for the Palm-size PC 
	- Microsoft eMbedded Visual Basic, version 3.0, on platform(s):
	   - Microsoft Windows CE version 2.11 for the Palm-size PC 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	WCELoad.exe is a patch that fixes a problem affecting the Palm-size PC devices
	running Windows CE version 2.11. The devices hang or reset during the
	self-registration process of ActiveX controls when they are installed through a
	packaged Application Install Wizard CAB file.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  WceLoad.exe
	  (http://download.microsoft.com/download/vb60ent/Patch/1/W9XNT4/EN-US/WCELoad.EXE)
	
	Release Date: Aug-27-1999
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	+---------------------+
	| FileName     | Size | 
	+---------------------+
	| Wcelupd.exe  | 33KB | 
	+---------------------+
	| Wce10003.bin | 49KB | 
	+---------------------+
	| Wce4000.bin  | 60KB | 
	+---------------------+
	| Readme.txt   | 2KB  | 
	+---------------------+
	
	TARGET DEVICE
	
	Palm-size PCs running Windows CE version 2.11
	
	PROBLEM DESCRIPTION
	
	Palm-size PC devices running Windows CE version 2.11 hang or reset during the
	self-registration process of ActiveX controls when they are installed within an
	Application Installation CAB file. This behavior occurs because the
	device-install program WCELoad.exe was not invoking CoInitializeEx before the
	self-registration process.
	
	UPDATE PACKAGE DESCRIPTION
	
	This package silently installs the fixed WCELoad.exe file to a connected
	Palm-size PC device. If the connected device is not a color Palm-size PC, or the
	device already has the fixed file, then the package exits immediately with a
	successful return code.
	
	USAGE
	
	Your desktop setup program needs to perform the following before invoking
	CEAppMgr to install the CAB files:
	
	1. Prompt the user to connect the device.
	
	2. Run the WCELupd.exe file and wait for it to complete.
	
	3. Examine the return code and handle it appropriately. In most cases, the only
	  error return code that needs to be handled is the "device disconnected"
	  return code 1.
	
	FILES TO REDISTRIBUTE
	
	The following three files comprise this update package, and must reside in the
	same directory:
	
	  WCELupd.exe
	  WCE10003.bin
	  WCE4000.bin
	
	RETURN CODES
	
	Following are the possible return codes from WCELupd.exe:
	
	  0 - Success
	  1 - Device disconnected
	  2 - Unsupported color Palm-size PC processor
	  3 - ActiveSync RAPI error
	  4 - Windows CE Services or ActiveSync not installed
	  5 - General error
	
	Additional query words: VBCE WceLoad PsPC PPC eVB
	
	======================================================================
	Keywords          : kbfile kbpatch kbAppSetup kbDeployment kbToolkit kbVBp600 kbGrpDSVB kbOSWinCE211 kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword2 kbVBeMbSearch kbWinCETKVBSearch kbWinCESearch
	Version           : :1.0,2.11,3.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
