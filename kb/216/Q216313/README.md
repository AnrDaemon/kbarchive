---
layout: page
title: "Q216313: XADM: Exchange Admin Unable to Map SIDs to Account Names After 5"
permalink: /kb/216/Q216313/
---

## Q216313: XADM: Exchange Admin Unable to Map SIDs to Account Names After 5

{% raw %}

	Article: Q216313
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fixkbbuglist
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server Administrator program can be installed and run
	from computers running Windows NT Workstation. If the workstation computer is in
	a domain with a one-way trust, such that the domain where the Exchange Server
	computers reside trusts the domain where the computers running Windows NT
	workstation reside, but the reverse is not true, the Exchange Server
	Administration program may not be able to administer the Exchange Key Management
	Server (KMS) features from these computers running Windows NT Workstation.
	
	When you attempt to view the KMS properties dialog box with the Exchange Server
	Administrator program, you will be prompted for the KMS password. After you type
	the password, a message box with the following error message may be displayed:
	
	  No mapping between account names and security IDs was done.
	
	This only occurs if any of the Exchange KMS administrator accounts are in the
	Exchange Server domain.
	
	CAUSE
	=====
	
	In Exchange Server 5.0, the Exchange Server Administrator program requests the
	account names of the KMS administrators. In Exchange Server 5.5, the Exchange
	Server Administrator program was requesting the security IDs (SIDs) of the KMS
	administrators. This required that the Exchange Server Administrator program map
	the SIDs back into names. Because the domain that the computers running Windows
	NT Workstation are in does not trust the domain the Exchange Server computers
	are in, the Exchange Server Administrator program will not ask the Exchange
	Server domain to map the SIDs to strings.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: KMS
	
	+------------------------+
	| File name | Version    | 
	+------------------------+
	| Admin.exe | 5.5.2549.0 | 
	+------------------------+
	
	
	WORKAROUND
	==========
	
	To work around this problem, you could set up a two-way trust between the two
	domains. A second workaround would be to move the computers running Windows NT
	Workstation into the same domain as the Exchange Server computers.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	======================================================================
	Keywords          : exc55 EXC55SP3Fix kbbuglist
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
