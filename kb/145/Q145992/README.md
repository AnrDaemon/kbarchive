---
layout: page
title: "Q145992: PRB: Global MFC DAO Objects Cause Assertions"
permalink: /kb/145/Q145992/
---

## Q145992: PRB: Global MFC DAO Objects Cause Assertions

{% raw %}

	Article: Q145992
	Product(s): Microsoft C Compiler
	Version(s): 4.00 4.10
	Operating System(s): 
	Keyword(s): kbDAOsearch kbDatabase kbMFC kbVC
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An assertion can occur on line 729, 732, or 1314 of Daocore.cpp when you define
	an MFC DAO object that has its destructor called after the call to
	CWinApp::ExitInstance.
	
	This will happen when an MFC DAO object is defined globally or as a member of a
	global object (like an MFC application's CWinApp-derived object).
	
	CAUSE
	=====
	
	CWinApp::ExitInstance() closes all open DAO workspaces by calling AfxDaoTerm()
	and removes them from the global workspace map. In the destructors for MFC DAO
	objects such as CDaoDatabase and CDaoRecordset, MFC tries to remove the
	workspace objects again.
	
	RESOLUTION
	==========
	
	Here are two workarounds:
	
	- Instead of using a global DAO object, define a global pointer to a DAO
	  object. Be sure to destroy the MFC object before CWinApp::ExitInstance().
	
	-or-
	
	- Explicitly assign the CDaoWorkspace object to the DAO object rather than
	  allowing MFC to create a CDaoWorkspace object implicitly. You can do this by
	  passing the workspace objects and database objects into the constructors of
	  the CDaoDatabase and CDaoRecordset objects respectively. Or you can
	  explicitly set the CDaoDatabase::m_pWorkspace and CDaoRecordset::m_pDatabase
	  variables before opening the CDaoDatabase or CDaoRecordset. Here is an
	  example:
	
	     CDaoWorkspace   wsp;
	     CDaoDatabase    db;
	     CMyDaoRecordset rs;
	
	     BOOL InitializeDBStuff()
	     {
	        db.m_pWorkspace=&wsp;
	        db.Open( _T("D:\\work\\assert.mdb") );
	        rs.m_pDatabase=&db;
	        rs.Open(dbOpenDynaset, _T("Select * from table1"));
	        rs.Close();
	        db.Close();
	     }
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: recordset 4.00 4.10
	
	======================================================================
	Keywords          : kbDAOsearch kbDatabase kbMFC kbVC 
	Technology        : kbAudDeveloper kbMFC
	Version           : 4.00 4.10
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
