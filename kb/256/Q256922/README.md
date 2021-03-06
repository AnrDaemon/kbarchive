---
layout: page
title: "Q256922: SMS: Components Don't Function After Upgrading Win9x to Win2000"
permalink: /kb/256/Q256922/
---

## Q256922: SMS: Components Don't Function After Upgrading Win9x to Win2000

{% raw %}

	Article: Q256922
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug
	Last Modified: 10-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After upgrading Microsoft Windows 9x clients to Microsoft Windows 2000, the
	Microsoft Systems Management Server client components do not function. For
	example, the Systems Management Server utility in the Control Panel does not
	work.
	
	CAUSE
	=====
	
	When you upgrade to Windows 2000, the registered and autostart client services
	are removed from the registry. The Systems Management Server files are saved on
	the computer, but without the client services, they cannot function.
	
	WORKAROUND
	==========
	
	There is no workaround for this issue; the Systems Management Server client must
	be removed and reinstalled.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
