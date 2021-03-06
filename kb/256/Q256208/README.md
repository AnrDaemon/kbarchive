---
layout: page
title: "Q256208: SMS: Query-Based Collection May Not Work Correctly on Child Site"
permalink: /kb/256/Q256208/
---

## Q256208: SMS: Query-Based Collection May Not Work Correctly on Child Site

{% raw %}

	Article: Q256208
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kberrmsg kbsms200 kbsms200bug
	Last Modified: 26-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a query-based collection on a parent site, all of the expected
	records are displayed. However, you may be unable to perform the rule evaluation
	on the child site and the following error message may be displayed:
	
	_com_error exception in MMC Admin UI!
	Description: 	Factory Enumeration Failure
	HRESULT : 	0xEEEE0001
	File : 		E:\OPALSP2\mmcadminui\Support\SMS_NMGR\NMGR_NodeData.cpp
	Line: 		272
	
	<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>
	
	Description: 	Error enumerating (select * from SMS_CM_RES_COLL_QPL0000F)
	HRESULT : 	0x80041010
	File : 		E:\OPALSP2\mmcadminui\Support\SMS_NWBM\NWBM_CWbemAsyncNodeFactory.cpp
	Line: 		358
	<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>
	
	Description: 	
	Error : 		WBEM_NO_ERROR
	Operation:	GetObject
	ParameterInfo:	SMS_CM_RES_COLL_QPL0000F
	Wbem error object:
	
	instance of __ExtendedStatus
	{
		Operation = "GetObject";
		ParameterInfo = "SMS_CM_RES_COLL_QPL0000F";
		ProviderName = "WinMgmt";
	};
	Entry Point : 	Result node factory error QUAKE1
	Operation : 	
	Command Line: 	C:\WINNT\System32\mmc.exe "D:\SMS\bin\i386\sms.msc" "____" "" "" "" "" "" "" ""
	Trace :
	
	CAUSE
	=====
	
	When the collection is opened, Systems Management Server (SMS) does not retrieve
	any rules to evaluate the collection because there are no matching records in
	the rules tables.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	Additional query words: prodsms fail fails
	
	======================================================================
	Keywords          : kberrmsg kbsms200 kbsms200bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
