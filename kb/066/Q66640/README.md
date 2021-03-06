---
layout: page
title: "Q66640: SAMPLE: Increasing the File Handle Limit with SetHandleCount"
permalink: /kb/066/Q66640/
---

## Q66640: SAMPLE: Increasing the File Handle Limit with SetHandleCount

{% raw %}

	Article: Q66640
	Product(s): Microsoft Windows Software Development Kit
	Version(s): 3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kbOSWin310 kbOSWin300 kb16bitonly
	Last Modified: 23-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows-based applications can access more than 20 files. To do this, call the
	SetHandleCount() function with the number of files needed for the application.
	The return value from this function specifies the exact number of handles that
	the application can use. Note that the maximum number of handles that can be
	requested is 255, and what is returned can be a number less than requested.
	
	There is a sample application named HANDLCNT in the Microsoft Download Center
	that demonstrates the use of SetHandleCount().
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  Handlcnt.exe
	  (http://download.microsoft.com/download/platformsdk/sample30/1/W31/EN-US/HANDLCNT.EXE)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	Every Windows-based application is given enough memory when it is loaded to
	access 20 file handles. This default setting is the same as the setting used in
	the C run-time libraries. Similarly, the first 5 handles are reserved for basic
	file I/O, as with any other MS-DOS-based application, leaving the other 15
	available for the Windows-based application to use.
	
	When you call SetHandleCount(), the file handle location in the application's
	program segment prefix (PSP) is expanded to reflect the number of files
	requested. Because the PSP is unique for every instance of every application,
	the change in the file handle count will be internal to the application that
	called SetHandleCount(). No other changes are made in the system. Furthermore,
	the number of files that may be opened by this application, set by
	SetHandleCount(), is not limited by the FILES environment variable, declared in
	the CONFIG.SYS file.
	
	To use these handles, you must also use the Windows file I/O routines (_lopen(),
	_lclose(), _lread(), and so forth). These routines are versions of the C
	run-time routines modified to accept a handle value greater than If the Windows
	file I/O functions do not offer enough flexibility, routines must be written by
	the ISV with the appropriate functionality using Int 21H calls. If Int 21H calls
	are to be used, we recommend that these calls be performed in a dynamic-link
	library (DLL). Doing this will make it easier to service the code in the future
	if significant changes are made with the Windows file I/O routines.
	
	If you want to use the C run-time functions instead of using the Windows file I/O
	routines or writing each routine separately, you must modify the C run-time code
	to increase the file handle limit. For more information on increasing the file
	limit, query in the C language Knowledge Base or consult the documentation
	supplied with the Microsoft C Compiler. Once the C run-time code has been
	modified, the C run-time routines can be used within the limit of file handles
	set during the modification. A modified C run-time routine will fail if it is
	passed a file handle value greater than the new limit that was set.
	
	The above approaches are the only acceptable methods of using more than the
	default 20 file handles in a Windows-based application. If you attempt to
	increase the number of files by calling Int 21H, Function 67H, important
	information will not be recorded in Windows and you will experience problems
	using file handles over the default number.
	
	Additional query words: HANDLCNT.EXE kbfile
	
	======================================================================
	Keywords          : kbfile kbsample kbOSWin310 kbOSWin300 kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : :3.0,3.1
	
	=============================================================================
	

{% endraw %}
