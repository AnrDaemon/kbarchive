---
layout: page
title: "Q120448: PC Adm: Microsoft Mail MAILMGR.DLL Version 3.2.0.4074 Update"
permalink: /kb/120/Q120448/
---

## Q120448: PC Adm: Microsoft Mail MAILMGR.DLL Version 3.2.0.4074 Update

{% raw %}

	Article: Q120448
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): kbgraphxlinkcritical
	Last Modified: 21-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft provides a replacement for the MAILMGR.DLL file that is included with
	version 3.2 of Microsoft Mail for Windows.
	
	For complete information about obtaining and installing the MAILMGR.DLL file, see
	the following sections:
	
	- To download the updated file
	
	- To update your MAILMGR.DLL file
	
	MORE INFORMATION
	================
	
	This update contains MAILMGR.DLL, a replacement for the MAILMGR.DLL file that is
	included with version 3.2 of Microsoft Mail for Windows. The replacement file
	provides additional enhancements to the original MAILMGR.DLL file.
	
	This replacement file resolves the following problem that can occur when you use
	version 3.2 of Microsoft Mail for Windows:
	
	- The Check Names function fails to properly resolve partial friendly names and
	  returns several selections when a unique resolution is possible. This
	  behavior is most obvious when the GAL is selected as the default address list
	  and the first and last name of the intended recipient begin with the same
	  letter.
	
	  NOTE: To resolve this problem, two .DLL files must be updated: the MAILMGR.DLL
	  file (update included in this update) and the MSSFS.DLL file (update included
	  in MSSFS.EXE on the MSL).
	
	To download the updated file
	----------------------------
	
	The following file is available for download from the Microsoft Download Center:
	
	  DownloadDownload Mailmgr.exe now
	  (http://download.microsoft.com/download/pcmail/Update/10/DOS/EN-US/Mailmgr.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	After you download MAILMGR.EXE to a clean directory, run it (by typing "mailmgr"
	(without the quotation marks) at the MS-DOS prompt) to extract the contents of
	the file. You should receive the following files:
	
	  MAILMGR.DLL (51,696 bytes, dated 07-21-94, 10:48 A.M.)
	  README.TXT
	
	To replace your MAILMGR.DLL file
	--------------------------------
	
	1. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <path>:\mailmgr.dll <destination> " (without the quotation
	  marks)
	
	  where <path> is the drive and directory where you ran the self
	  extracting MAILMGR.EXE file and <destination> is the drive and
	  directory where your MAILMGR.DLL file currently resides. For example, if you
	  ran the self-extracting file from the TEST directory on drive D, and your
	  MAILMGR.DLL file is located in the MAILEXE directory on drive C, type the
	  following command:
	
	  " copy d:\test\mailmgr.dll c:\mailexe " (without the quotation marks)
	
	2. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <mailexe>\setup.inf <mailexe>\setupinf.old " (without the
	  quotation marks)
	
	  where <mailexe> is the complete path to the directory containing the
	  Microsoft Mail for Windows SETUP.EXE program. For example, if SETUP.EXE is
	  located in the MAILEXE directory on drive C, type the following command:
	
	  " copy c:\mailexe\setup.inf c:\mailexe\setupinf.old " (without the quotation
	  marks)
	
	3. Using any text editor, edit the SETUP.INF file. In the [MSMAIL] section,
	  replace the following line
	
	  1, mailmgr.dll,,,, 1993-03-09, !DECOMPRESS,, OLDER, !READONLY,,,,, SHARED,
	  51632,,,, 3.2.0.4027,
	
	  with:
	
	  1, mailmgr.dll,,,, 1994-07-21, !DECOMPRESS,, OLDER, !READONLY,,,,, SHARED,
	  51696,,,, 3.2.0.4074,
	
	  Save the file and close the text editor.
	
	  NOTE: For these changes to affect the entire network, each existing user must
	  run Setup again.
	
	Additional query words: 3.20 wga
	
	======================================================================
	Keywords          : kbgraphxlinkcritical 
	Technology        : kbMailSearch kbZNotKeyword3 kbMail320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
