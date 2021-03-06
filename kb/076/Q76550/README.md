---
layout: page
title: "Q76550: FIX: Undocumented Separator Property of a VB Menu Item"
permalink: /kb/076/Q76550/
---

## Q76550: FIX: Undocumented Separator Property of a VB Menu Item

{% raw %}

	Article: Q76550
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0,2.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition for Windows, version 2.0 
	- Microsoft Visual Basic Standard Edition for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may encounter an undocumented property for menu items that allows you to
	toggle between the caption and a separator bar. A separator bar in a menu is a
	horizontal line that separates menu item groups.
	
	CAUSE
	=====
	
	Microsoft did not intend to leave the Separator property in the Visual Basic
	product.
	
	RESOLUTION
	==========
	
	The Separator property is not documented in Visual Basic's manuals or online
	Help. Microsoft recommends that you not use the Separator property in your
	Visual Basic applications. The Separator property no longer exists in Visual
	Basic version 3.0.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the products listed above. This
	problem was corrected in Microsoft Visual Basic version 3.0 for Windows by
	removing the Separator property.
	
	MORE INFORMATION
	================
	
	Separator Property (Applies to Menu Items)
	------------------------------------------
	
	Description: Denotes if a menu item is a separator bar. Prevents
	            or allows the value of the Caption property of the
	            menu item to be displayed versus a separator bar.
	
	Usage:       [form.][menuitem.]Separator[= boolean%]
	
	Remarks:     The Separator property settings are as follows:
	
	            Setting       Description
	            -----------------------------------------------------
	            True (-1)     Disables the display of the value of
	                          the Caption property as the menu item.
	                          Instead, a separator bar is displayed.
	
	            False (0)     (Default) for all other menu items.
	                          The menu item will display the value
	                          of the Caption property for that item.
	
	            When a menu item is created in the menu design window,
	            the value of its separator property defaults to 0 unless
	            the caption of that menu item is set to a dash (-), in
	            which case, the Separator property defaults to -1 and a
	            separator bar is displayed for that item instead of the
	            value of the Caption property.
	
	Additional query words: buglist1.00 buglist2.00 fixlist3.00 2.00 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper
	Version           : :1.0,2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
