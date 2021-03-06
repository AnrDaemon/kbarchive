---
layout: page
title: "Q195688: WD97: Accented or Extended Characters Lost in Mail Merge"
permalink: /kb/195/Q195688/
---

## Q195688: WD97: Accented or Extended Characters Lost in Mail Merge

{% raw %}

	Article: Q195688
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word97 kbmerge
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If you use a text file (*.txt) as a data source for a mail merge, extended
	characters such as accented characters are replaced by symbols with no
	similarity to the expected characters. However, if you open the data source text
	file in the editor used to create the text file, the characters appear
	correctly.
	
	CAUSE
	=====
	
	This problem occurs when you use text files created in a Microsoft Windows-based
	word-processing program such as Microsoft Notepad or Microsoft Word.
	
	In a text file, each character is saved as a numeric value. Windows-based
	programs usually use the numeric values in the American National Standards
	Institute (ANSI) character set. MS-DOS programs, however, use the numeric values
	from the ASCII character set, which does not include the extended characters.
	Therefore, MS-DOS programs use the OEM character set to define the extended
	characters.
	
	When Word sees a text file as the mail merge data source, it assumes that it was
	created in an MS-DOS based program and translates the characters using the ASCII
	character set. As a result the extended (accented) characters are lost.
	
	This behavior does not occur in Microsoft Word 2000.
	
	MORE INFORMATION
	================
	
	To correctly use your text file (*.txt) as a Microsoft Word mail merge data
	source, use any of the following methods.
	
	Method 1: Convert the Text File to Word Document Format
	-------------------------------------------------------
	
	To convert the text file to Word document format, follow these steps:
	
	1. Open the text file (*.txt) in Word. The accented characters should be
	  visible.
	
	2. Save the file as a Word document (*.doc).
	
	3. Use this file as the mail merge data source.
	
	Method 2: Convert the Text File to Microsoft Excel Format
	---------------------------------------------------------
	
	To convert the text file to Excel format, follow these steps:
	
	1. Open the text file (*.txt) in Excel. This starts the Text Import Wizard.
	
	2. Follow the instructions in the wizard and then save the file as an Excel
	  Workbook (*.xls) file.
	
	3. Use this Excel file as the mail merge data source.
	
	Method 3: Modify the Registry Entries for Word
	----------------------------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To change the default behavior of mail merge text import, modify one of the
	following keys in the Windows Registry.
	
	1. Quit Word.
	
	2. On the Start menu, click Run.
	
	3. In the Run box, type "REGEDIT" (without the quotation marks), and click OK.
	
	4. Locate either of the following registry entries:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\3.0\Engines\Text
	
	  -or-
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\3.5\Engines\Text
	
	5. Click to select the CharacterSet entry in the right pane.
	
	6. On the Edit menu, click Modify.
	
	7. In the Value Data box, type "ANSI" (without the quotation marks) and press
	  ENTER.
	
	8. Quit the Registry Editor and start Word.
	
	Word now assumes that all text files that you use as mail merge data sources come
	from a Windows-based program. Word therefore uses the ANSI character set to
	import extended characters correctly.
	
	NOTE: Extended characters in text files that were created in MS-DOS-based
	programs will be imported incorrectly, since this workaround applies only to
	Microsoft Windows-based programs.
	
	Additional query words: incorrect wrong
	
	======================================================================
	Keywords          : kbdta word97 kbmerge 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
