---
layout: page
title: "Q257779: FIX: Printer Dialog of DataReport PrintReport Is Always Portrait"
permalink: /kb/257/Q257779/
---

## Q257779: FIX: Printer Dialog of DataReport PrintReport Is Always Portrait

{% raw %}

	Article: Q257779
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbReportWriter kbVBp kbVBp600bug kbDataEnv kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using the PrintReport method of the DataReport object and passing True for
	the first parameter, the Printer dialog box always defaults to Portrait even if
	you set the printer's default orientation to Landscape in the Printers folder on
	Microsoft Windows.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Change the default printer's default page orientation to Landscape in the
	  Printers folder on Windows.
	
	2. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	3. Add a CommandButton control to Form1.
	
	4. Paste the following code into Form1's code window:
	
	  Private Sub Command1_Click()
	     DataReport1.PrintReport True
	  End Sub
	
	5. From the Project menu, select Add Data Environment to add DataEnvironment1 to
	  the project.
	
	6. In DataEnvironment1, right-click Connection1, and then choose Properties. Set
	  the Properties of Connection1 to be the following:
	
	   - On the Provider tab, set Provider to Microsoft Jet 4.0 OLE DB Provider.
	
	   - Click Next.
	
	   - On the Connection tab, set the database name to NWIND.MDB.
	
	   - Click Test Connection to make sure you are connected to the database.
	
	   - Click OK.
	
	7. Right-click Connection1 and choose Add Command to add Command1.
	
	8. Right-click Command1 and select Properties. Set the properties of Command1 to
	  be the following:
	
	   - On the General tab, change the Database object to Table.
	
	   - Drop down the Object Name combo box and select Employees.
	
	   - Click OK.
	
	9. From the Project menu, select Add Data Report. DataReport1 is added by
	  default.
	
	10. Set the properties of DataReport1 to be the following:
	
	   - Set the DataSource property to DataEnvironment1.
	
	   - Set the DataMember property to Command1.
	
	   - Set the ReportWidth property to 11520 (8 inches).
	
	   - Set the LeftMargin property to 1440 (1 inch).
	
	   - Set the RightMargin property to 1440 (1 inch).
	
	11. If you add ReportWidth, LeftMargin, and RightMargin, the total report width
	  is 10 inches, which is correct size for the Landscape orientation on
	  standard letter size paper.
	
	12. Press the F5 key to run the program.
	
	13. Click the CommandButton that brings up the Printer dialog box. Note that the
	  Page Orientation in the Printer dialog box is Portrait.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbReportWriter kbVBp kbVBp600bug kbDataEnv kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
