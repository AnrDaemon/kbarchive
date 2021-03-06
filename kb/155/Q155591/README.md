---
layout: page
title: "Q155591: BUG: Cannot Set Access Memo Field to NULL with Snapshots"
permalink: /kb/155/Q155591/
---

## Q155591: BUG: Cannot Set Access Memo Field to NULL with Snapshots

{% raw %}

	Article: Q155591
	Product(s): Microsoft C Compiler
	Version(s): 1.50 1.51 1.52c
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 30-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.5, 1.51, 1.52c 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using a Snapshot recordset with the CRecordset class, if you delete the
	contents of a CString mapped to a memo field in a Microsoft Access database,
	nothing is actually deleted in the database. In other words, the data that
	previously existed in the field remains in that field. However, the recordset
	still shows that the field has been changed to null but it has only been changed
	in the cache of the cursor library, not the database.
	
	CAUSE
	=====
	
	A problem exists in the ODBC cursor library which is used by default in MFC.
	
	RESOLUTION
	==========
	
	This problem was resolved with the ODBC Cursor Library that ships with Visual
	C++ 4.0 for 32-bit ODBC components and remains unresolved for 16-bit ODBC
	components.
	
	If possible, use dynasets in your application. If you cannot use dynasets, then
	you need to replace "empty" memo fields with a single space. The code below
	shows how to use this solution with a CRecordView derived class.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	The code below is from a CRecordView derived class using a recordset for an
	Access data source, which has a memo field that maps to m_Memo.
	
	      void CMyView::DoDataExchange(CDataExchange* pDX)
	      {
	          CRecordView::DoDataExchange(pDX);
	
	          // Data Members --> Dialog
	          if (pDX->m_bSaveAndValidate == 0)
	          {
	              if( m_pSet->m_Memo.GetLength() == 0 )
	              {
	                  m_pSet->m_Memo = " ";
	              }
	          }
	
	          //{{AFX_DATA_MAP(CMyView)
	          ...
	          //}}AFX_DATA_MAP
	
	          // Dialog --> Data Members
	          if (pDX->m_bSaveAndValidate != 0)
	          {
	              if( m_pSet->m_Memo.GetLength() == 0 )
	              {
	                 m_pSet->m_Memo = " ";
	              }
	          }
	      }
	
	Additional query words: kbmfc kbdatabase kbodbc kbvc150bug kbvc151bug kbvc152bug
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVCsearch kbAudDeveloper kbvc150 kbVC151
	Version           : 1.50 1.51 1.52c
	
	=============================================================================
	

{% endraw %}
