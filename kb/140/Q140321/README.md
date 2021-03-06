---
layout: page
title: "Q140321: HOWTO: Set the Default Choice in a List Box or Combo Box"
permalink: /kb/140/Q140321/
---

## Q140321: HOWTO: Set the Default Choice in a List Box or Combo Box

{% raw %}

	Article: Q140321
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDesigner kbvfp300 kbvfp500 kbvfp600
	Last Modified: 09-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When including a combo box or list box on a form, developers often want to have
	default selection as something other than the first item in the list. To do
	this, set the Value property to a value contained in the list.
	
	MORE INFORMATION
	================
	
	By setting the Value property of a combo box or list box to a value contained in
	the list, you ensure that the item becomes selected (highlighted) as the default
	selection. All items contained in a combo box or list box are stored as a text
	variables, as such any reference to a field or variable for setting the value
	property must be converted to a character value. If the list contains multiple
	columns the Value property must contain a value in the bound column.
	
	Step-by-Step Example
	--------------------
	
	1. Using the Customer table form the Testdata Database, create a from and add a
	  list box.
	
	2. Set the following properties for the list box:
	
	     BoundColumn = 1
	     ColumnCount = 2
	     ColumnWidths = 63,150
	     RowSource = Customer.Cust_id,Title
	     RowSourceType = 6-Fields
	
	3. In the Init event of the list box, add the following line of code:
	
	     This.Value='FOLIG'
	
	4. Save and run the form, the default (highlighted) item will be the first item
	  in the list containing "FOLIG" in the first column.
	
	This method of locating the first instance of a value in a list will only find
	the first instance of a value. Items in a list are usually unique, if duplicate
	values are displayed in the list, you may need to locate for a value contained
	in another column either visible or not.
	
	Additional query words: ColumnWidths ListBox ComboBox Selected
	
	======================================================================
	Keywords          : kbDesigner kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
