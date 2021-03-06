---
layout: page
title: "Q233426: Running Microsoft FrontPage 2000 Comments and Corrections"
permalink: /kb/233/Q233426/
---

## Q233426: Running Microsoft FrontPage 2000 Comments and Corrections

{% raw %}

	Article: Q233426
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 07-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Running Microsoft FrontPage 2000 ISBN 1-57231-947-x 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book Running Microsoft FrontPage 2000, ISBN
	1-57231-947-x.
	
	The following topics are covered:
	
	- CD-ROM: L&H Audio Cafe Lite Is Incompatible With FrontPage 2000
	
	- Page xl: Step 6 is Incorrect
	
	- Page xxxi: Incorrect Steps To Copy Files To Hard Disk
	
	- Page 12: Figure 1-6 Needs Caption
	
	MORE INFORMATION
	================
	
	CD-ROM: L&H Audio Cafe Lite Is Incompatible With FrontPage 2000
	---------------------------------------------------------------
	
	When trying to install "L&H Audio Cafe Lite" from the companion CD, you will
	receive the following error even if you have plenty of room on the target
	drive:
	
	"Not enough disk space on target drive while attempting to copy files. To
	continue, first free disk space on the target drive and then click OK."
	
	L&H Audio Cafe Lite is not compatible with FrontPage 2000. It's compatible
	only with FrontPage 97 and FrontPage 98.
	
	
	Page xl: Step 6 is Incorrect
	----------------------------
	
	Change the second paragraph of step 2 to the following:
	
	"If you decided in step 5..."
	
	
	Page xxxi: Incorrect Steps To Copy Files To Hard Disk
	-----------------------------------------------------
	
	On page xxxi, the directions to copy files to the hard drive at a command prompt
	contain too many sets of quotation marks.
	
	Change:
	"-On Windows 95 or Windows 98:
	xcopy32 d:\rfp2000\*.* " "c:\My Documents\My Webs\rfp2000\" /s
	
	-On Windows NT:
	xcopy d:\rfp2000\*.* " "c:\My Documents\My Webs\rfp2000\" /s
	
	To:
	"-On Windows 95 or Windows 98:
	xcopy32 d:\rfp2000\*.* "c:\My Documents\My Webs\rfp2000\" /s
	
	-On Windows NT:
	xcopy d:\rfp2000\*.* "c:\My Documents\My Webs\rfp2000\" /s
	
	
	Page 12: Figure 1-6 needs caption
	---------------------------------
	
	On page 12, the figure at the top of the page is missing a caption and figure
	number. Please add the following in the left margin, top-aligned with the top of
	the figure:
	
	FIGURE 1-6.
	The New dialog box contains templates you can use to create a Web page.
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: 1-57231-947-x eubook eurun fp2000
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
