---
layout: page
title: "Q193692: Exchange Server Eval Copy Will Not Send Mail"
permalink: /kb/193/Q193692/
---

## Q193692: Exchange Server Eval Copy Will Not Send Mail

{% raw %}

	Article: Q193692
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server Training 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The 120-day evaluation copy of Microsoft Exchange Server 5.5 will appear to
	install successfully. However, no messages will be sent or received; sent
	messages will remain in the user's Outbox.
	
	The following event ID 1182 is logged in the application event log:
	
	  Stop Error in Event App Log, Event ID 1182
	  Thank you for your participation in the Microsoft Exchange Server beta
	  program.
	  Your license to use this beta version of the Microsoft Exchange Server
	  software has expired. Contact Microsoft Corporation.
	
	CAUSE
	=====
	
	The evaluation software expired on September 1, 1998. If your computer is set to
	a date after September 1, 1998, the evaluation software will not allow messages
	to be sent.
	
	RESOLUTION
	==========
	
	To resolve this problem, a supported fix that corrects this problem is now
	available from Microsoft. This fix has been posted to the following Internet
	location:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/Eval-Fix/
	
	NOTE: This address should appear on one line.
	
	To install this fix, follow these steps:
	
	1. Download Evalstri.exe to a temporary location on your hard drive.
	
	2. Unzip the file by typing "Evalstri.exe" (without the quotation marks) at the
	  command prompt.
	
	3. Stop the Microsoft Exchange Information Store Service.
	
	4. Go to the Microsoft Exchange Server bin folder. By default, this folder is
	  C:\exchsrvr\Bin.
	
	5. Rename the file, Store.exe to Store.bak.
	
	6. Copy the new Store.exe into the Microsoft Exchange Server bin folder.
	
	7. Restart the Microsoft Exchange Information Store Service.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft Exchange Server
	Training kit.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q193485 XADM: Exchange Server 5.5 120-Day Evaluation Copy Expiring
	
	
	Additional query words: 1-57231-709-4
	
	======================================================================
	Keywords          :  
	Technology        : kbMSPressSearch kbZNotKeyword2
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
