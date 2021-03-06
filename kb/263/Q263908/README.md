---
layout: page
title: "Q263908: XADM: Information Store Crash in EcReplFolderMessagesUnpack"
permalink: /kb/263/Q263908/
---

## Q263908: XADM: Information Store Crash in EcReplFolderMessagesUnpack

{% raw %}

	Article: Q263908
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical kbExchange2000SP1
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	- Microsoft Exchange 2000 Server 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Store.exe process stops responding (crashes), perhaps on more than one
	server in the organization. If Dr. Watson is enabled, and Exchange symbols are
	installed, the stack of the crashing thread is similar to the following:
	
	  
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  0277fd9c 00535952 0277fe30 0277fdec 073f1ae0 0000003f store!EcReplFolderMessagesUnpack [omap]  (FPO: [EBP 0x00000000] [2,35,4])
	
	In addition, the following events may be logged:
	
	  Event 3089 Warning
	
	  Error 0x80004002 occurred while processing an incoming replication message.
	
	-and-
	
	  Event 3079 Error
	
	  Unexpected replication thread error 0x80004002.
	  EcReplFolderMessagesUnpack
	  EcReplMessageUnpack
	  FReplRcvAgent
	
	CAUSE
	=====
	
	This behavior is caused by a public folder replication message that has been
	changed by an anti-virus program, adding an attachment which reports that a
	virus has been removed. The resulting message is in an invalid format, causing
	the store to crash.
	
	
	RESOLUTION
	==========
	
	Exchange 2000 Server
	--------------------
	
	To resolve this problem, obtain the latest service pack for Exchange 2000 Server.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q301378 XGEN: How to Obtain the Latest Exchange 2000 Server Service Pack
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191914 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  x86: DownloadDownload Q248838engi.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25443)
	  Alpha: DownloadDownload Q248838enga.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25444)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	STATUS
	======
	
	Exchange 2000 Server
	--------------------
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange 2000 Server.
	This problem was first corrected in Exchange 2000 Server Service Pack 1.
	
	Exchange Server 5.5
	-------------------
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem was first corrected in Exchange Server 5.5 Service Pack 4.
	
	Additional query words: 3079 3089
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical kbExchange2000SP1Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange2000Search kbExchange2000Serv
	Version           : :5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
