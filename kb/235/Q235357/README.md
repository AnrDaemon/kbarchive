---
layout: page
title: "Q235357: PRB: FoxPro ODBC Driver Replaced by Visual FoxPro ODBC Driver"
permalink: /kb/235/Q235357/
---

## Q235357: PRB: FoxPro ODBC Driver Replaced by Visual FoxPro ODBC Driver

{% raw %}

	Article: Q235357
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:1.0,2.0,2.1,2.1 (GA),2.1 SP1,2.1 SP2,3.0,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbDatabase kbODBC kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport
	Last Modified: 04-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC Driver for Visual FoxPro, versions 1.0, 2.0, 3.0, 4.0, 5.0 
	- Microsoft ODBC Driver for Visual FoxPro (Build 6.00.8281.00), version 6.0 
	- Microsoft Data Access Components versions 2.1, 2.1 (GA), 2.1 SP1, 2.1 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When attempting to create a DSN using the installable ISAM ODBC Driver for
	FoxPro, the following message appears:
	
	  The Microsoft FoxPro driver is no longer supported, and has been replaced by
	  the Microsoft Visual FoxPro driver.
	
	When attempting to use an existing DSN or create a DSN-less connection based on
	the FoxPro installable ISAM ODBC Driver, the following message appears:
	
	  Could not find installable ISAM
	
	CAUSE
	=====
	
	ODBC access to FoxPro 2.x tables was previously supported in version 3.5x and
	earlier of the installable ISAM ODBC driver (ODBCJT32.DLL). With the release of
	Microsoft Data Access Components (MDAC) 2.1 and the Visual FoxPro ODBC Driver,
	ODBC access to FoxPro 2.x tables using the installable ISAM driver (ODBCJT32.DLL
	version 4.00 and later) is no longer supported.
	
	RESOLUTION
	==========
	
	Use the Microsoft Visual FoxPro ODBC driver (version 6.00.), which is supported
	with MDAC 2.1. To do this, it will be necessary to take the following actions.
	
	1. Delete the DSN created using the FoxPro 2.x installable ISAM driver.
	
	2. Create a new DSN using the Visual FoxPro ODBC Driver.
	
	3. Set the Data Source Name property so that it is the same as the DSN that used
	  the installable ISAM driver.
	
	4. Under the Database Type options, select "Free Table Directory."
	
	5. In the Path field, enter the path to the FoxPro 2.x tables that will be used
	  as the ODBC data source.
	
	6. Click Options to display the Driver panel and deselect the NULL checkbox.
	  Because FoxPro 2.x tables will not accept NULL values, this step will ensure
	  that the ODBC driver does not attempt to insert NULL values into the FoxPro
	  2.x tables.
	
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	MDAC 2.1 installs with the following Microsoft Products:
	
	- Microsoft SQL Server 7.0
	- Microsoft SQL Server 6.5 Service Pack 5a
	- Microsoft Office 2000
	- Microsoft Windows 98, Second Edition
	- Microsoft Visual Studio 6.0 Service Pack 3
	
	Steps to Reproduce Behavior
	---------------------------
	
	Depending on the action being taken, one of two messages appears.
	
	Example 1:
	
	This example attempts to create a new DSN using the FoxPro installable ISAM ODBC
	driver:
	
	1. Install the Microsoft Data Access Components 2.1. Note that SQL Server 7.0
	  installs MDAC 2.1.
	
	2. Open the ODBC Administrator and click the Add button.
	
	3. Select the ODBC Driver captioned "Microsoft FoxPro Driver (*.dbf)."
	
	4. Click Finish.
	
	5. The following message appears:
	
	  The Microsoft FoxPro driver is no longer supported, and has been replaced by
	  the Microsoft Visual FoxPro driver.
	
	Example 2:
	
	This example attempts to access an existing DSN, created using the Microsoft
	FoxPro installable ISAM ODBC driver:
	
	1. Open the ODBC Administrator and select a DSN based on the "Microsoft FoxPro
	  Driver (*.dbf)" ODBC Driver.
	
	2. Click Configure.
	
	3. The following message appears:
	
	  Could not find installable ISAM
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbODBC kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport 
	Component         : JET
	Technology        : kbVFPsearch kbAudDeveloper kbODBCSearch kbMDACSearch kbMDAC210 kbMDAC210SP1 kbMDAC210SP2 kbODBCVFP100 kbODBCVFP200 kbODBCVFP300 kbODBCVFP400 kbODBCVFP500 kbODBCVFP600828100
	Version           : WINDOWS:1.0,2.0,2.1,2.1 (GA),2.1 SP1,2.1 SP2,3.0,4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
