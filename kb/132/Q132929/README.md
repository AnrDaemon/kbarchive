---
layout: page
title: "Q132929: PRB: &quot;DDE Connection Failed&quot; When Viewing a File"
permalink: /kb/132/Q132929/
---

## Q132929: PRB: &quot;DDE Connection Failed&quot; When Viewing a File

{% raw %}

	Article: Q132929
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe310 kbSSafe304
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0 
	- Microsoft SourceSafe for Windows, versions 3.04, 3.1 
	- Microsoft SourceSafe for Windows NT, versions 3.04, 3.1 
	- Microsoft SourceSafe for MS-DOS, versions 3.04, 3.1 
	- Microsoft SourceSafe for Macintosh, versions 3.04, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Occasionally, you may get the error message "DDE Connection Failed" when you
	view a file within SourceSafe. Other errors may be returned, such as "Unable to
	Execute..." or "Error Opening...".
	
	CAUSE
	=====
	
	This problem occurs when SourceSafe cannot open a file with its default editor.
	This may be due to the editor file being moved, deleted, or mapped to a
	different network drive.
	
	RESOLUTION
	==========
	
	To work around this problem, you must tell SourceSafe what editor to use for a
	specified file:
	
	1. Open the SS.INI file for that user (NOTE: The SRCSAFE.INI file may be used,
	  but it is not suggested since each machine may be configured differently).
	
	2. Add the line to tell SourceSafe the correct associations and file locations.
	  Example:
	
	  .DOC = C:\MSOFFICE\WINWORD\WINWORD.EXE %1
	
	  NOTE: The %1 is needed to tell the DDE connection that this is the file that
	  should be opened.
	
	  IMPORTANT: If the applications path contains spaces, you must enclose the
	  entire path in quotes (""), such as:
	
	  .DOC = "C:\MS OFFICE\WINWORD\WINWORD.EXE" %1
	
	3. Close and restart SourceSafe for the changes to take effect.
	
	If you still have problems opening a file for viewing, then make sure that the
	following have been checked:
	
	1. The path to the .EXE is correct.
	
	2. The .EXE file exists.
	
	3. The extension is correct.
	
	4. The extension line was put above any section headers in the INI file.
	
	This technique can also be used to override any associations that may be made
	with files. For instance, a user may want to view a .C file in Notepad, rather
	than starting Visual C++ every time.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe310 kbSSafe304 
	Technology        : kbHWMAC kbOSMAC kbSSafeSearch kbAudDeveloper kbZNotKeyword2 kbZNotKeyword3 kbSSafe304 kbSSafe304DOS kbSSafe310 kbSSafe310DOS kbSSafe304Mac kbSSafe310Mac kbSSafe400 kbSSafe500 kbSSafe304NT kbSSafe310NT
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
