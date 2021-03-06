---
layout: page
title: "Q285991: OLE DB Provider for DB2 Error Transferring More Than 32,763 Rows"
permalink: /kb/285/Q285991/
---

## Q285991: OLE DB Provider for DB2 Error Transferring More Than 32,763 Rows

{% raw %}

	Article: Q285991
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbDSupport kbsna400sp3 kbsna400sp4
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0 SP3, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using SNA Server's OLE DB Provider for DB2 to transfer more than
	32,763 rows of data between Microsoft SQL Server and IBM DB2 for MVS, the
	following error may occur:
	
	  Error at Destination for Row number 32764.
	  Errors encountered so far in this task:1
	  Conversational protocol error.
	  SQLSTATE : HY000
	  SQLCODE : -343
	
	CAUSE
	=====
	
	As the OLE DB Provider for DB2 transfers data, it increments a correlator ID for
	each element in a chain. If the correlator ID reaches 0X7FFF, DB2 for MVS
	returns a protocol violation error when the correlator ID is incremented to the
	next value of 0X8000. The OLE DB Provider for DB2 returns the error noted in the
	"Symptoms" section.
	
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft SNA Server version 4.0 service pack that contains this
	fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+------------------------------------+
	| File name   | Date       | Time    | 
	+------------------------------------+
	| Db2serv.exe | 01/17/2001 | 12:00PM | 
	+------------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version 4.0
	Service Pack 3 and Service Pack 4.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbsna400sp3 kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400SP3 kbSNAServ400SP4
	Version           : :4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
