---
layout: page
title: "Q153023: BUG: Adding PIF Files in SetupWiz Step 7 Copies Actual Files"
permalink: /kb/153/Q153023/
---

## Q153023: BUG: Adding PIF Files in SetupWiz Step 7 Copies Actual Files

{% raw %}

	Article: Q153023
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 27-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After selecting a file with a .PIF extension to add to the list of files in step
	7 of the Setup Wizard, the actual .PIF file is not added. Instead, the file that
	the PIF file points to is added. For example, selecting the DOSPRMPT.PIF file
	actually adds COMMAND.COM to the list of included files. This problem only
	occurs with the 32-bit version of the Setup Wizard running under the Windows 95
	or Windows 98 operating systems. This problem does not occur on Windows NT
	(3.51).
	
	
	RESOLUTION
	==========
	
	To work around this problem, manually add any files with a .PIF extension to a
	template file to be used by the Setup Wizard following these step-by step
	instructions:
	
	1. Start the Setup Wizard and proceed normally until step 7.
	
	2. Click the Save Template button and create a template (.VBZ) file. Exit the
	  Setup Wizard.
	
	3. Open this .VBZ file in a text editor such as Notepad, and add a line for each
	  PIF file to be included. The only change needed is to the first parameter to
	  the path of the PIF file. Some sample added lines are listed below:
	
	  File17=C:\ENROLL\ENROLL.ICO,0,$(AppPath),,|32760|,-1,0,0,0,,,0
	  File18=C:\ENROLL\MSTRS.EXE,0,$(AppPath),,|32760|,-1,0,0,0,,,0
	  File19=C:\ENROLL\README.HLP,0,$(AppPath),,|32760|,-1,0,0,0,,,0
	  File20=C:\ENROLL\TRAIN.HLP,0,$(AppPath),,|32760|,-1,0,0,0,,,0
	
	4. Restart the Setup Wizard and click the Open Template button to load the
	  modified template file. Proceed normally through the rest of the Setup Wizard
	  steps.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps To Reproduce Behavior
	---------------------------
	
	1. Start the 32-bit version of the Visual Basic 4.0 Setup Wizard.
	
	2. Select the CALC.VBP sample project located in VB\SAMPLES\CALC as the project
	  for which to create setup media.
	
	3. Choose Next repeatedly until Step 7 of the Wizard is reached.
	
	4. On step 7, click the Add Files button. Change to the Windows directory, and
	  add the file called DOSPRMPT.PIF.
	
	5. Note that the file that was actually added was COMMAND.COM, not DOSPRMPT.PIF.
	
	Additional query words: kbVBp400bug kbDSupport kbdss kbdsstools kbWizard kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : :4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
