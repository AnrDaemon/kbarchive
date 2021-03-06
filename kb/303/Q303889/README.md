---
layout: page
title: "Q303889: MX Record Failover Does Not Occur When 4xx Error Occurs"
permalink: /kb/303/Q303889/
---

## Q303889: MX Record Failover Does Not Occur When 4xx Error Occurs

{% raw %}

	Article: Q303889
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): 2000,2000 SP1,2000 SP2
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbnetwork kbtool kbSysAdmin kbWin2000PreSP3Fix kbWin2000sp3fix
	Last Modified: 15-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2 Server 
	- Microsoft Windows versions 2000, 2000 SP1, 2000 SP2 Advanced Server 
	- Microsoft Exchange 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an external DNS resolver is used on your Simple Mail Transfer Protocol
	(SMTP) virtual server, the next MX record is not tried when the host for the
	first MX record returns a "4xx" error.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, click the following article number to view the article
	in the Microsoft Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time   Version        Size     File name
	  ----------------------------------------------------
	  09/13/01  10:52  5.0.2195.4051  320,784  Aqueue.dll
	  09/13/01  10:52  5.0.2195.4051   66,832  Mailmsg.dll
	  09/13/01  10:52  5.0.2195.4051   38,160  Ntfsdrv.dll
	  09/13/01  10:52  5.0.2195.4236  435,472  Smtpsvc.dll
	
	
	NOTE: Before you apply the hotfix that is described in this article, install
	Windows 2000 Service Pack 2 (SP2) and Exchange 2000 Service Pack 1 (SP1).
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Windows 2000 Service Pack 3.
	
	
	Additional query words: kbMgmtAdmin esm
	
	======================================================================
	Keywords          : kbenv kberrmsg kbnetwork kbtool kbSysAdmin kbWin2000PreSP3Fix kbWin2000sp3fix 
	Technology        : kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbwin2000ServSearch kbwin2000Search kbExchangeSearch kbExchange2000Search kbWinAdvServSearch kbWin2000AdvServSP2 kbWin2000AdvServSP1 kbwin2000ServSP1 kbwin2000ServSP2 kbExchange2000Serv
	Version           : :2000,2000 SP1,2000 SP2
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
