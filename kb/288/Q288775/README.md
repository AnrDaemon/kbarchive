---
layout: page
title: "Q288775: PRB: Authentication Dialog Box When Exchange Accessed with MAPI"
permalink: /kb/288/Q288775/
---

## Q288775: PRB: Authentication Dialog Box When Exchange Accessed with MAPI

{% raw %}

	Article: Q288775
	Product(s): Microsoft Exchange
	Version(s): 1.0,1.21,4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbCDO kbMAPI kbMsg kbGrpDSMsg kbDSupport kbExchange2000SP1Fix
	Last Modified: 12-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	- Extended Messaging Application Programming Interface (MAPI), version 1.0 
	- Microsoft Exchange 2000 Server 
	- Collaboration Data Objects (CDO), version 1.21 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use MAPI or CDO to log on to an Exchange server, a dialog box prompts
	you for credentials. This dialog box has the caption "Enter Password" and fields
	for "User Name", "Domain Name", and "Password".
	
	CAUSE
	=====
	
	The account that the code is running under is in a domain that is not trusted by
	the Exchange Server's domain, or is not logged on to a domain at all.
	
	RESOLUTION
	==========
	
	MAPI and CDO rely on the Exchange Message Store (EMS) provider to communicate
	with Exchange. The EMS provider uses the credentials of the user that is
	currently logged on to establish a remote procedure call (RPC) connection with
	the Exchange server. If these credentials are insufficient to establish the RPC
	connection, the provider prompts the user for additional credentials. There is
	no way to pass credentials to the provider programmatically.
	
	There are three ways to avoid this dialog box:
	
	- Join the domain in which the Exchange server is operating. In other words,
	  run the code under an account that is in the Exchange server's domain.
	
	- Establish a trust relationship between the domain that your computer is
	  running in and the domain of the other computer. If the two domains trust
	  each other, they can exchange authentication information.
	
	- Use the SendKeys method or a similar method to fill in the blanks on the
	  credentials dialog box. Note that this method is not recommended, because a
	  subtle change in the layout of the dialog box may break it.
	
	The last option is the equivalent of manually filling out the credentials dialog
	box. Note that because no authentication has yet taken place, there is no way to
	encrypt this information; therefore, it is transmitted as plain text to the
	Exchange Server.
	
	Additional query words: MAPILogon MAPILogonEx Session logon box authentication
	
	======================================================================
	Keywords          : kbCDO kbMAPI kbMsg kbGrpDSMsg kbDSupport kbExchange2000SP1Fix 
	Technology        : kbAudDeveloper kbCDOsearch kbMAPISearch kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword kbZNotKeyword2 kbExchange2000Search kbCDO121 kbExchange2000Serv kbMAPIExt
	Version           : :1.0,1.21,4.0,5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
