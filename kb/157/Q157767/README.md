---
layout: page
title: "Q157767: Vfpodbc5.exe Visual FoxPro ODBC Driver Version 5.0"
permalink: /kb/157/Q157767/
---

## Q157767: Vfpodbc5.exe Visual FoxPro ODBC Driver Version 5.0

{% raw %}

	Article: Q157767
	Product(s): Microsoft FoxPro
	Version(s): 5.0,5.0a
	Operating System(s): 
	Keyword(s): kbfile kbinterop kbAutomation kbvfp500
	Last Modified: 10-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Vfpodbc5.exe is a patch that contains the Visual FoxPro ODBC driver version 5.0
	
	The Visual FoxPro ODBC Driver provides extremely fast access to Visual FoxPro
	5.0, Visual FoxPro 3.0, and FoxPro 2.x tables, as well as Visual FoxPro 5.0 and
	3.0 databases. It supports all database rules, triggers, and default values and
	conforms with the ODBC level 1 API.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Vfpodbc5.exe
	  (http://download.microsoft.com/download/vfox50/Patch/1/W9X/EN-US/Vfpodbc5.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To install the Visual FoxPro ODBC driver 5.0, run Vfpodbc5.exe. The following
	information is an excerpt from the Visual FoxPro ODBC Driver 5.0 Update Release
	Notes. The complete Release Notes are installed with the updated driver.
	
	What is New in this release
	---------------------------
	
	- Query performance is 20% faster.
	
	- Vfpodbc.dll is smaller (from 1.20MB to ~835KB).
	
	- The SET commands (see Help file for a list of supported SET commands) are now
	  supported.
	
	- VERSION( ) is supported through stored procedures.
	
	- Local views are read-only.
	
	- If you insert or update a table with a logical field (a column with a SQL_BIT
	  data type), you can now use 1 (true) and 0 (false) to store a value in a
	  field. When comparing values or in an expression, you must use .T. (true) and
	  .F. (false).
	
	- The 16-bit version of Microsoft Query (version 1.0) now works with the Visual
	  FoxPro ODBC Driver.
	
	- SQLGetInfo( ) and SQL_FILE_USAGE now returns SQL_FILE_QUALIFIER for both
	  database and free table data sources.
	
	Known Issues
	------------
	
	- If you insert, delete, or update a Visual FoxPro table via the Visual FoxPro
	  ODBC driver, you might get a "Trigger Failed" message. Check for unsupported
	  commands in the trigger.
	
	- INDEX ON is not supported in this release.
	
	- If a table is opened exclusively and the same table is accessed by another
	  user with SET EXCLUSIVE OFF, then the Visual FoxPro ODBC Driver returns the
	  error "Cannot Open File" instead of "File is in use by another."
	
	- MSQuery returns a "Cannot Access Table" error when creating a table with a
	  field name that starts with a number. For example, the field name "1995
	  Sales" is not allowed. Visual FoxPro does not allow the creation of field
	  names that begin with a number, but MSQuery does.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbinterop kbAutomation kbvfp500 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : :5.0,5.0a
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
