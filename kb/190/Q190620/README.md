---
layout: page
title: "Q190620: PRB: Error 3622 Open SQL Server Table with Identity Column"
permalink: /kb/190/Q190620/
---

## Q190620: PRB: Error 3622 Open SQL Server Table with Identity Column

{% raw %}

	Article: Q190620
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbATLComposite kbDatabase kbVBp600bug kbGrpDSVBDB kbDSupport
	Last Modified: 03-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to open a Dynaset in Visual Data Manager (or Visual Basic sample
	project VisData) against a Microsoft SQL Server 6.5 table that contains an
	Identity column, you may receive the following error message:
	
	  Error 3622 - You must use the dbSeeChanges option with OpenRecordset when
	  accessing a SQL Server table that has an IDENTITY column.
	
	RESOLUTION
	==========
	
	To work around this problem, set the Options property for the data control to
	dbSeeChanges (512). To change the Options property on a data control to the
	proper value, use one of the following two methods:
	
	- In the design environment, make sure that the data control is the selected
	  item on your form. Then, go to the properties sheet, and set the Options
	  property to 512.
	
	- In the run-time environment, use the following line of code to set the
	  Options property of a data control named data1:
	
	  data1.options = dbSeeChanges
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	You need to recompile VisData.vbp, create a new VisData.exe, and then copy it to
	the VisualBasic default folder.
	
	You can modify the VisData sample to avoid the error. There are two places that
	you need to make the changes: where you open a recordset from the Database
	Window, and where you execute a SQL statement.
	
	1. In VISDATA.BAS, under the OpenTable() function, change:
	
	     Set rsTmp=gdbCurrentDB.OpenRecordset(rName, dbOpenDynaset)
	
	  -to-
	
	     Set rsTmp=gdbCurrentDB.OpenRecordset(rName,dbOpenDynaset, dbSeeChanges)
	
	2. In VISDATA.BAS, under the OpenQuery() function, change:
	
	     Set rsTmp = qdfTmp.OpenRecordset(dbOpenDynaset)
	
	  -to-
	
	     Set rsTmp = qdfTmp.OpenRecordset(dbOpenDynaset, dbSeeChanges)
	
	3. After Making Changes to VISDATA.BAS, recompile the VISDATA project and copy
	  the compiled executable to the Visual Basic directory (which is \Program
	  Files\Microsoft Visual Studio\Vb98 by default in Visual Basic 6.0)
	
	NOTE: There may be other areas of VisData code that would require changes based
	on which part of the VisData Tool you are using.
	For testing purposes, table IColTest is created in Pubs database with one
	Identity column and one VarChar column. To create a table and index in SQL
	Server, select Pubs database, then place the following Create Table T-SQL in the
	SQL window of ISQL/W and execute it:
	
	     Create Table IColTest
	             (Id_Col int Identity, Name VarChar(30) Null)
	     Create Unique Index IIndex on IColTest(Id_Col)
	
	WARNING: ANY USE BY YOU OF THE CODE MODIFICATIONS PROVIDED IN THIS ARTICLE IS AT
	YOUR OWN RISK. Microsoft provides this code modification "as is" without
	warranty of any kind, either express or implied, including but not limited to
	the implied warranties of merchantability and/or fitness for a particular
	purpose. Microsoft does not support modifications to sample applications or
	tools.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbATLComposite kbDatabase kbVBp600bug kbGrpDSVBDB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
