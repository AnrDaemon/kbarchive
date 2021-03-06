---
layout: page
title: "Q131752: PRB: Form Variable Unknown After Running Form Inside App"
permalink: /kb/131/Q131752/
---

## Q131752: PRB: Form Variable Unknown After Running Form Inside App

{% raw %}

	Article: Q131752
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you create a form and then run that form from the Command window, the
	variable that contains the instance of the form object is, in fact, in memory.
	If the function TYPE('myform') is placed in the Debug window, the value "O" for
	object is displayed. When running the same form in an application, however, the
	variable is not shown when memory is displayed and the function TYPE('myform')
	returns "U" for undefined.
	
	CAUSE
	=====
	
	When you use the DO FORM command, you create both an instance variable and a
	form object.
	
	When you use the DO FORM command from the Command window, the instance variable
	is by default public. That's why you always see it.
	
	When you use the DO FORM command in a program, the instance variable is private
	by default. When control returns to the program to the line following the DO
	FORM command, the variable is out of scope and the TYPE function returns "U."
	
	WORKAROUND
	==========
	
	Set the WindowType property of the form to modal to keep the object in scope, or
	create a public variable, as in this example:
	
	     PUBLIC myform
	     DO FORM myform
	
	Make the program (the .PRG file) the main file in the project, and rebuild the
	application.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	While the scope of the variable created within the application is limited to the
	application, the variable created when the form is run from the Command window
	is global within the Visual FoxPro development environment.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form using the Form Designer.
	
	2. Place the TYPE('myform') function in the Debug window.
	
	3. Run the form. The Debug window shows "O."
	
	4. Display memory, and verify that <myform> is listed as a variable.
	
	5. Add the form to a project.
	
	6. Build an application.
	
	7. Use the CLEAR ALL command to clear memory.
	
	8. Run the application. The Debug window displays "U." Display memory and
	  <myform> is not listed as a variable, although the form is active.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
