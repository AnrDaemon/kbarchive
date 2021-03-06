---
layout: page
title: "Q282780: XCON:  MTA Database Format and Structure"
permalink: /kb/282/Q282780/
---

## Q282780: XCON:  MTA Database Format and Structure

{% raw %}

	Article: Q282780
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the most important features of the Microsoft Exchange
	Server message transfer agent (MTA) database and their relationship to each
	other. This information is useful to complete successful MTA disaster recovery.
	
	MORE INFORMATION
	================
	
	The MTA is made up of a service, static files, and a flat file database. The
	service is displayed as "Microsoft Exchange Message Transfer Agent" in the
	Services tool. In Task Manager, the service is displayed as "Emsmta.exe". The
	following registry hive stores many of the settings for the MTA:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeMTA
	
	The MTA static files tell the MTA how to handle various message formats and
	communication methods. These files also include the configuration files, logs,
	and event messages. These files are called "static" because they do not change
	during normal operation of the MTA. These files are periodically updated with
	service packs and hotfixes, and they should never be modified or deleted. The
	following registry hive contains the location of the static files:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeMTA\Parameters\MTA
	  Run Directory
	
	The following registry hive contains the MTA database location:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeMTA\Parameters\MTA
	  database path
	
	The MTA database is made up of core files (which are required for starting the
	MTA), queue files, and message files. All MTA database files have a file name
	pattern of DB<nnnnnn>.DAT, where <nnnnnn> is a hexadecimal number.
	
	The first 38 database files (Db000001.dat to Db000026.dat) are the core database
	files. They are core files because the MTA does not start if these files are not
	present, or if one or more of these files is corrupted.
	
	NOTE: To determine if the core database files have been corrupted, check the file
	size. If the file is 0 bytes in size, it has been corrupted.
	
	The core database files have not changed since Exchange Server 5.5 was shipped;
	therefore, you can replace these files in a disaster recovery scenario by
	copying the same files from the Exchange Server installation CD-ROM. These files
	are located in the following folders:
	
	- <CD_Drive>:\Server\Setup\i386\Bootenv (for Intel platforms)
	
	- <CD_Drive>:\Server\Setup\Alpha\Bootenv (for Alpha platforms)
	
	Queue files are MTA database files that represent a queue, such as a queue to the
	Internet Mail Service. In the Microsoft Exchange Server Administrator program,
	each MTA has a queue for the local private information store (MDB), the local
	public information store (MDB), all location connectors or gateways, and for
	each server in the local site. These are all outbound queues. When you use
	Performance Monitor, the MTA Work Queue is also displayed. This queue is the
	only inbound queue. The MTA Work Queue manages all inbound messages that have
	not been routed to an outbound queue. The MTA Work Queue also manages
	distribution list expansion, and delayed delivery messages.
	
	The Exchange Server MTA makes a distinction between secured and non-secured
	outbound queues. Non-secured queues exist only in memory when the MTA is
	running. Messages queued to a non-secured queue may be rerouted if the connector
	or server to which it is queued is not accepting delivery. Examples of
	non-secured queues are:
	
	- X.400 Connector
	
	- Site Connector
	
	- Dynamic Remote Access Server (RAS) Connector
	
	- Private MDB
	
	- Public MDB
	
	When the MTA is shut down, it retains no knowledge of the non-secured queues;
	therefore messages that are routed to non-secured queues must be reevaluated for
	routing when the MTA starts again.
	
	Alternatively, secured queues are represented as files in the MTA database. After
	messages are routed to a secured queue, they are not rerouted by the MTA. In
	fact, the MTA considers messages routed to secured queues as successfully
	delivered. Even if you shut down the MTA and restart it, you cannot force the
	MTA to reevaluate messages that have been queued to a secured queue. Examples of
	secured queues are:
	
	- Internet Mail Service
	
	- MS Mail Connector
	
	- Microsoft Exchange Connector for Lotus cc:Mail
	
	- Microsoft Exchange Connector for Lotus Notes
	
	- Microsoft Exchange Connector for Novell GroupWise
	
	- Microsoft Exchange Connector for SNADS
	
	- Microsoft Exchange Connector for IBM OfficeVision/VM (PROFS)
	
	- MS Mail Directory Synchronization (DXA)
	
	- Third-party Exchange Development Kit (EDK) gateways such as Pager Connectors
	  and FAX Connectors
	
	Finally, most of the rest of the files in the MTA database are messages.
	
	How to Identify  Secured Queues
	-------------------------------
	
	To identify .dat files that are secured queues, run the following command:
	
	  mtacheck /v /f mtacheck.log
	
	After you run this command, open Mtacheck.log, and look for mention of queues at
	the beginning of the log. The following text is an example of an Mtacheck.log
	file:
	
	  
	
	  Checking queue XAPIWRKQ (id 01000020)
	
	  Checking queue OOFINFOQ (id 01000025)
	
	  Checking queue REFDATQ (id 01000026)
	
	  Checking queue MTAWORKQ (id 01000027)
	
	  Checking queue /O=ORG/OU=SITE/CN=CONFIGURATION/CN=CONNECTIONS/CN=MS MAIL CONNECTOR 
	  (EXSERV1) (id 0100002C)
	
	  Checking queue /O=ORG/OU=SITE/CN=CONFIGURATION/CN=SERVERS/CN=EXSERV1/CN=MICROSOFT 
	  DXA (id 0100002F)
	
	  Checking queue /O=ORG/OU=SITE/CN=CONFIGURATION/CN=CONNECTIONS/CN=INTERNET MAIL 
	  CONNECTOR (EXSERV1) (id 0100002D)
	
	  Starting object integrity checks
	 Checking object 03000002 - OK, on queue 01000026
	 Checking object 0A000003 - OK, on queue 01000020
	 Checking object 0B000004 - OK, on queue 01000020
	 Checking object 0B000005 - OK, on queue 01000020
	 Checking object 0C000006 - OK, on queue 01000020
	 Checking object 0C000007 - OK, on queue 01000020
	 Checking object 06000008 - OK, on queue 01000020
	 Checking object 06000009 - OK, on queue 01000020
	 Checking object 0600000A - OK, on queue 01000020
	 Checking object 0600000B - OK, on queue 01000020
	 Checking object 0600000C - OK, on queue 01000020
	 Checking object 0600000D - OK, on queue 01000020
	 Checking object 0600000E - OK, on queue 01000020
	 Checking object 0600000F - OK, on queue 01000020
	 Checking object 06000010 - OK, on queue 01000020
	 Checking object 06000011 - OK, on queue 01000020
	 Checking object 06000012 - OK, on queue 01000020
	 Checking object 06000013 - OK, on queue 01000020
	 Checking object 06000014 - OK, on queue 01000020
	 Checking object 06000015 - OK, on queue 01000020
	 Checking object 09000016 - OK, on queue 01000020
	 Checking object 09000017 - OK, on queue 01000020
	 Checking object 09000018 - OK, on queue 01000020
	 Checking object 09000019 - OK, on queue 01000020
	 Checking object 0900001A - OK, on queue 01000020
	 Checking object 0900001B - OK, on queue 01000020
	 Checking object 0600001C - OK, on queue 01000020
	 Checking object 0600001D - OK, on queue 01000020
	 Checking object 0600001E - OK, on queue 01000020
	 Checking object 0600001F - OK, on queue 01000020
	 Checking object 06000021 - OK, on queue 01000020
	 Checking object 06000022 - OK, on queue 01000020
	 Checking object 06000023 - OK, on queue 01000025
	 Checking object 09000024 - OK, on queue 01000025
	
	  Database clean, no errors detected.
	
	In this example, there are three secured queues:
	
	- One for the MS Mail Connector (0100002C)
	
	- One for MS Mail Directory Synchronization (0100002F)
	
	- One for the Internet Mail Service (0100002D)
	
	You can change the queue identification numbers to .dat file names by changing
	the "01" to "DB", and then adding ".dat" to the end of the queue ID number. For
	example, the Internet Mail Service queue is a file named "Db00002D.dat". In this
	example, you can also see that Db000027.dat is the MTA Work Queue.
	
	The Db000001.dat file has special significance. This file represents a queue that
	has knowledge of all the queues, both secure and non-secure, on this MTA. You
	should be careful to preserve the Db000001.dat file because if you lose this
	file, all messages in the secured queues may be lost.
	
	Relationship of Files in the MTA Database
	-----------------------------------------
	
	- Db000001.dat is the "Super queue", or the "Queue of queues". It keeps track
	  of the queue ID numbers for all queues in the MTA database, including
	  standard queues (XAPIWRKQ, OOFINFOQ, REFDATQ, and MTAWORKQ) and secured
	  queues.
	
	- Secured queues are assigned a unique queue ID number the first time the MTA
	  is started (or the first time you run MTACHECK) after you configure an EDK
	  gateway (for example, Internet Mail Connector (IMC), MS Mail Connector, DXA,
	  cc:Mail Connector, GroupWise Connector, Notes Connector, SNADS Connector,
	  PROFS Connector, Pager, Fax, and so on). This queue ID number and its
	  associated queue file (Db0000xx.dat) persist even when the MTA is shut down.
	
	- All messages routed to secured queues keep a record of which queue they have
	  been routed to. This record is in the form of the queue ID number for the
	  secured queue. For this reason, you can use the mtacheck /v command to find
	  out which queue the individual messages are on.
	
	- After a message has been routed to a secured queue, the MTA considers the
	  message successfully routed and it does not try to reroute the message.
	  Therefore, if the MTA is stopped and restarted, it does not reevaluate the
	  routing for messages that have previously been routed to secured queues.
	
	Based on the information in this section, in a disaster recovery scenario the
	following rules apply:
	
	- If a secured queue file is deleted, but the Super queue remains intact, and
	  you can run MTACHECK to re-create the secured queue. When you do so, no data
	  loss occurs, because all messages that are previously routed to the secured
	  queue still point to the old secured queue file (which has now been
	  regenerated).
	
	  NOTE: When MTA files are deleted, you may have unexpected results. Therefore,
	  always back up the MTA database before you work on it.
	
	- If the Super queue is deleted, regardless of whether the secured queues have
	  been deleted or not, data loss likely occurs. When a new Super queue is
	  created (for example, you restore it from the Bootenv folder from the
	  Exchange Server CD-ROM), the next time you start the MTA, or run MTACHECK,
	  new secured queue ID numbers may be generated that may differ from the
	  previous secured queue ID numbers. These new secured queue ID numbers render
	  the previous secured queue ID numbers invalid. Therefore, a message that has
	  been routed to the previous secured queue is no longer deliverable because
	  the queue that the message should be on no longer exists, and the MTA does
	  not reroute or reevaluate the routing for those messages.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbinfo
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
