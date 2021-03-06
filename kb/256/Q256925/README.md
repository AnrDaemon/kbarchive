---
layout: page
title: "Q256925: BUG: INSERT INTO View w/Default Value Does Not Work as Expected"
permalink: /kb/256/Q256925/
---

## Q256925: BUG: INSERT INTO View w/Default Value Does Not Work as Expected

{% raw %}

	Article: Q256925
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbDatabase kbSQL kbvfp600 KbDBFDBC kbGrpDSFox kbDSupport kbCodeSnippet kbSQLProg
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using an updateable view to a table with a default value in the view but
	not in the table, the value appears in the view but is not saved in the table.
	
	RESOLUTION
	==========
	
	1. Use the APPEND BLANK command and then the REPLACE command instead of the
	  (SQL) INSERT statement.
	2. Specify the default value in the table instead of in the view.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Create a program and paste following code into file, then run the program:
	
	  SET MULTILOCKS ON
	  CLOSE ALL
	  CLEAR
	  ERASE TestDB.d??
	  ERASE TestTable.*
	  CREATE DATABASE TestDB
	  CREATE TABLE TestTable (iID I, cData c(10))
	  CREATE SQL VIEW "View1" AS SELECT * FROM TestDB!TestTable
	  DBSETPROP('VIEW1', 'View', 'UpdateType', 1)
	  DBSETPROP('VIEW1', 'View', 'WhereType', 3)
	  DBSETPROP('VIEW1', 'View', 'FetchMemo', .T.)
	  DBSETPROP('VIEW1', 'View', 'SendUpdates', .T.)
	  DBSETPROP('VIEW1', 'View', 'UseMemoSize', 255)
	  DBSETPROP('VIEW1', 'View', 'FetchSize', 100)
	  DBSETPROP('VIEW1', 'View', 'MaxRecords', -1)
	  DBSETPROP('VIEW1', 'View', 'Tables', 'testdb!TestTable')
	  DBSETPROP('VIEW1', 'View', 'Prepared', .F.)
	  DBSETPROP('VIEW1', 'View', 'CompareMemo', .T.)
	  DBSETPROP('VIEW1', 'View', 'FetchAsNeeded', .F.)
	  DBSETPROP('VIEW1', 'View', 'FetchSize', 100)
	  DBSETPROP('VIEW1', 'View', 'Comment', "")
	  DBSETPROP('VIEW1', 'View', 'BatchUpdateCount', 1)
	  DBSETPROP('VIEW1', 'View', 'ShareConnection', .F.)
	  *!* Field Level Properties for VIEW1
	  * Props for the VIEW1.iid field.
	  DBSETPROP('VIEW1.iid', 'Field', 'KeyField', .T.)
	  DBSETPROP('VIEW1.iid', 'Field', 'Updatable', .T.)
	  DBSETPROP('VIEW1.iid', 'Field', 'UpdateName', 'testdb!TestTable.iid')
	  DBSETPROP('VIEW1.iid', 'Field', 'DataType', "I")
	  DBSETPROP('VIEW1.iid', 'Field', 'DefaultValue', "RECCOUNT()+1")
	  * Props for the VIEW1.cdata field.
	  DBSETPROP('VIEW1.cdata', 'Field', 'KeyField', .F.)
	  DBSETPROP('VIEW1.cdata', 'Field', 'Updatable', .T.)
	  DBSETPROP('VIEW1.cdata', 'Field', 'UpdateName', 'testdb!TestTable.cdata')
	  DBSETPROP('VIEW1.cdata', 'Field', 'DataType', "C(10)")
	  CLOSE TABLES ALL
	  SELECT 0
	  USE View1
	  * Insert with values for both fields
	  INSERT INTO View1 (iID, cData) VALUES (1, "Test1")
	  * Append Blank with Replace for cData only
	  APPEND BLANK
	  REPLACE cData WITH "Test2"
	  * Insert with value for cData only
	  INSERT INTO View1 (cData) VALUE ("Test3")
	  ?
	  ? "Listing of View1"
	  LIST
	  ?
	  SELECT TestTable
	  ? "Listing of TestTable"
	  LIST
	  CLOSE ALL 2
	  ?
	  ? "Reopening table"
	  USE TestDB!View1
	  ? "Listing of View1"
	  LIST
	  ?
	  SELECT TestTable
	  ? "Listing of TestTable"
	  LIST
	
	The program creates a database called TESTDB, a table called TestTable, and an
	updateable view called View1. View1 contains a default value expression of
	RECCOUNT()+1 for the iId field.
	
	The program will then do the following:
	
	- INSERT a record into the view, supplying values for both fields
	- INSERT a record into the view, supplying only a value for the character field
	  cData
	- APPEND BLANK and REPLACE cData with a value
	- List out the records in the view and the table
	- Close all files
	- Open the view
	- List out the records in the view and the table
	
	In the first set of listings on the screen, the third record in View1 has a value
	in the iId field while the iId field in the third record in TestTable is zero.
	In the second set of listings, both View1 and TestTable have zero in the iId
	field of the third record.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbSQL kbvfp600 KbDBFDBC kbGrpDSFox kbDSupport kbCodeSnippet kbSQLProg 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
