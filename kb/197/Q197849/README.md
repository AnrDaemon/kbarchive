---
layout: page
title: "Q197849: WD97: How to Open the Last Document Edited When You Start Word"
permalink: /kb/197/Q197849/
---

## Q197849: WD97: How to Open the Last Document Edited When You Start Word

{% raw %}

	Article: Q197849
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacro word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The bottom of the File menu lists the most recent files that have been saved or
	loaded in chronological order (the last file saved or opened appears first).
	This list of files is commonly referred to as the Most Recently Used (MRU)
	list.
	
	After you start Word, if you want to open the last file saved or opened, you can
	manually click the first file listed on the MRU list on the File menu, or you
	can have Word automatically open the file when you start Word by either
	modifying the Word command line or creating an AutoExec macro.
	
	MORE INFORMATION
	================
	
	To automatically open the last document edited when you start Word, use one of
	the following methods:
	
	Method 1: Use the "/mFile1" Switch on the Command Line
	------------------------------------------------------
	
	1. Right-click the Start button, and then click Explore.
	
	2. In Explorer, expand the Windows folder by clicking the plus (+) sign to the
	  left of the Windows folder. Expand the Start Menu folder, and then click the
	  Programs folder.
	
	3. In the Programs folder, right-click the shortcut for Microsoft Word, and then
	  click Properties.
	
	4. In the Properties dialog box, select the Shortcut tab. Add "/mFile1" (without
	  the quotation marks) to the Target line. For example, if you are using the
	  default Word 97 folder, change the Target line so that it looks like this:
	
	  C:\Program Files\Microsoft Office\Winword.exe /mFile1
	
	  NOTE: There is no space between the /m and File1.
	
	
	Method 2: Use an AutoExec Macro
	-------------------------------
	
	1. On the Tools menu, point to Macro, and then click Macros.
	
	2. In the Macros dialog box, type "AutoExec" (without the quotation marks) in
	  the Macro Name box, and then click Create.
	
	3. In the macro editing window, create the following macro:
	
	        Sub Autoexec()
	           RecentFiles(1).Open
	        End Sub
	
	4. On the File menu, click Close and Return to Microsoft Word.
	
	Additional query words: switch start-up parameters arguments startup
	
	======================================================================
	Keywords          : kbmacro word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
