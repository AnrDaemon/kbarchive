---
layout: page
title: "Q289877: Create a Query in SMS Server That Returns All Computers"
permalink: /kb/289/Q289877/
---

## Q289877: Create a Query in SMS Server That Returns All Computers

{% raw %}

	Article: Q289877
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbConfig kbMMC kbServer kbsms200 kbCollections kbInventory kbQuery kbsmsAdmin
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to create a query in your Systems Management Server
	(SMS) version 2.0 administrator console to return information about all
	computers that do not have a particular file installed.
	
	MORE INFORMATION
	================
	
	To create a query that returns information about all computers that do not have
	a particular file installed, you must first create a query that can detect all
	computers that have a selected file installed. In the following example, the
	file is named Mynotepad.exe. To create a query that displays all computers that
	contain the Mynotepad.exe file:
	
	1. In the SMS Administrator console, right-click the Queries node. Click New,
	  and then click Query.
	
	2. Give the new query a name and click the "Edit Query Statement" button.
	
	3. On the General tab, click the Star icon to add a new property.
	
	4. In the Results Properties dialog box, click the Select button, and then
	  specify System Resource for the attribute class and NetBIOS Name for the
	  attribute. (There is no need to specify an alias except for your own
	  readability.)
	
	5. On the General tab, click to select the "Omit duplicate rows" check box so
	  that duplicate entries in the results are not returned.
	
	6. On the Criteria tab, click the Star icon to create a new criteria.
	
	7. In the Criterion Properties dialog box, click the Select button. In Attribute
	  Class, click either Software Files or Software Product. If the attribute
	  class is Software Files, click File Name. Or, if the attribute class is
	  Software Product, click Product Name. (This example only uses the Software
	  Files and File Name settings for this query.)
	
	8. The operator must remain at the "is equal to" default and the value must be
	  the file name. The Values button can pull up all values, but it can be slow
	  if there is an enormous number of values to be returned.
	
	9. Click OK until the query is saved in the administrator console. Right-click
	  the query and click Run Query to view the results. You now have a list of the
	  computers that have the file specified. You are going to be using it to
	  create the list of computers that do not have the specified file installed.
	
	If you look at the query syntax in the SMS administrator console, it should
	resemble the following example:
	
	select distinct SMS_R_System.NetbiosName from SMS_R_System inner join
	SMS_G_System_SoftwareFile on SMS_G_System_SoftwareFile.ResourceID =
	SMS_R_System.ResourceId where SMS_G_System_SoftwareFile.FileName =
	"mynotepad.exe"
	
	To create the query that can display the computers that do not have a particular
	file installed, begin the same procedure that you used to create a query to find
	an installed file:
	
	1. In the SMS administrator console, right-click the Queries node. Click New,
	  and then click Query.
	
	2. Give the new query a name and click the "Edit Query Statement" button.
	
	3. On the General tab, click the Star icon to add a new property.
	
	4. In the Results Properties dialog box, click the Select button, and then
	  specify System Resource for the attribute class and Netbios Name for the
	  attribute. (There is no need to specify an alias except for your own
	  readability.)
	
	5. On the General tab, click to select the "Omit duplicate rows" check box so
	  that duplicate entries in the results are not returned.
	
	6. On the Criteria tab, click the Star icon to create a new criteria.
	
	7. In the Criterion Properties dialog box, specify Sub-selected values for the
	  Criterion Type.
	
	8. In the Criterion Properties dialog box, click the Select button. In Attribute
	  Class, click either Software Files or Software Product. If the attribute
	  class is Software Files, click File Name. Or, if the attribute class is
	  Software Product, click Product Name. (This example only uses the Software
	  Files and File Name settings for this query.) The operator must be changed to
	  "is not in".
	
	9. Click the Browse button at this point to select the previously created query
	  that finds all computers that have a file installed. This imports the query
	  syntax directly into the Sub-object window.
	
	If you examine the query syntax for this second query in the SMS administrator
	console, it may resemble the following example:
	
	select distinct Name from SMS_R_System where Name not in (select distinct
	SMS_R_System.Name from SMS_R_System inner join SMS_G_System_SoftwareFile on
	SMS_G_System_SoftwareFile.ResourceID = SMS_R_System.ResourceID where
	SMS_G_System_SoftwareFile.FileName = "mynotepad.exe") order by Name
	
	When you run this query, it returns to the Results window information about all
	computers that do not have this particular file installed.
	
	NOTE: If your software inventory is not set up to detect the file type you are
	searching for, it may not be returned. A search by product name is more accurate
	than a search by file name.
	
	Additional query words: prodsms mynotepad exe
	
	======================================================================
	Keywords          : kbConfig kbMMC kbServer kbsms200 kbCollections kbInventory kbQuery kbsmsAdmin 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
