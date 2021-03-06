---
layout: page
title: "Q165096: WD97: Cannot Record Macro to Set Options in Customize Dialog Box"
permalink: /kb/165/Q165096/
---

## Q165096: WD97: Cannot Record Macro to Set Options in Customize Dialog Box

{% raw %}

	Article: Q165096
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacro kbusage kbmacroexample word8 kbwordvba word97kbfaq
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to record a macro to set options in the Customize dialog box
	(on the Tools menu, click Customize), the recorded macro is blank.
	
	CAUSE
	=====
	
	The only actions recorded when accessing values in the Customize dialog box
	are:
	
	  Adding and deleting toolbars.
	
	  -and-
	
	  Adding, deleting, moving, or copying toolbar buttons, menu items, and
	  commands.
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	You can use the following Visual Basic for Applications sample to display large
	toolbar buttons and ScreenTips on all command bars:
	
	     Sub TurnOnCustomOptions()
	       With CommandBars
	           .LargeButtons = True
	           .DisplayTooltips = True
	           .DisplayKeysInTooltips = True
	        End With
	     End Sub
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbmacro kbusage kbmacroexample word8 kbwordvba word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
