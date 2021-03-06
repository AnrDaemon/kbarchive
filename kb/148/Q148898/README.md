---
layout: page
title: "Q148898: How to Make Batch Mode Setup Install Minimum Files"
permalink: /kb/148/Q148898/
---

## Q148898: How to Make Batch Mode Setup Install Minimum Files

{% raw %}

	Article: Q148898
	Product(s): Microsoft FoxPro
	Version(s): 3.00 3.00b
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 20-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	After performing an Administrative Setup to a network directory, you can perform
	a batch mode installation (SETUP /Q) that does a minimum install rather than a
	complete install. The steps below describe how to do this.
	
	MORE INFORMATION
	================
	
	An Administrative Setup creates a network directory structure containing the
	files suitable for installing Visual FoxPro to network clients. You can automate
	the client installation by running Setup.exe in a batch mode. This is
	accomplished by connecting to the network directory containing the
	Administrative Setup files and running Setup.exe with the /Q command line
	parameter. By default, this will perform a complete install. To perform a
	minimum install instead, you need to modify the following three files in the
	Administrative Setup directory:
	
	  Foxset16.stf
	  Foxset32.stf
	  Foxset95.stf
	
	You can edit these files with most text editors. However, the MS-DOS Editor
	(Edit.com) should not be used because it changes tabs to spaces.
	
	Below are the two lines that need to be changed. The change involves changing the
	second column in the indicated line to Yes or No, as needed. Note that
	<tab> indicates where the tab characters should be in each line.
	
	1. Change the second column in the following line from Yes to No.
	
	  Change this line:
	
	     13<tab>Yes<tab>&Complete<tab>Install all files for Microsoft Visual
	     FoxPro<tab>Group<tab>26 28 29 30 31 32 33<tab>"foxsetup.dll,
	     103"<tab><tab><tab><tab>
	
	  to this line:
	
	     13<tab>No<tab>&Complete<tab>Install all files for Microsoft Visual
	     FoxPro<tab>Group<tab>26 28 29 30 31 32 33<tab>"foxsetup.dll,
	     103"<tab><tab><tab><tab>
	
	2. Change the second column in the following line from No to Yes.
	
	  Change this line:
	
	     15<tab>No<tab>&Laptop (Minimum)<tab>Install just the minimum set of
	     files needed to run Microsoft Visual FoxPro.<tab>Group<tab>26<tab>
	     "foxsetup.dll, 105"<tab><tab><tab><tab>
	
	  to this line:
	
	     15<tab>Yes<tab>&Laptop (Minimum)<tab>Install just the minimum set of
	     files needed to run Microsoft Visual FoxPro.<tab>Group<tab>26<tab>
	     "foxsetup.dll, 105"<tab><tab><tab><tab>
	
	REFERENCES
	==========
	
	For more information about installation scripts, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q119357 OFF: "How to Create a Custom Installation Script" (WC1046)
	
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : 3.00 3.00b
	
	=============================================================================
	

{% endraw %}
