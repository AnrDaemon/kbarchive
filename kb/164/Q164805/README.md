---
layout: page
title: "Q164805: XADM: Contents of This Public Folder Currently Unavailable"
permalink: /kb/164/Q164805/
---

## Q164805: XADM: Contents of This Public Folder Currently Unavailable

{% raw %}

	Article: Q164805
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you restore the public store (Pub.edb) from a backup to a NEW server, and
	you attempt to access the content of one of the restored public folders, the
	following error message may appear:
	
	  The folder could not be opened. The contents of this public folder are
	  currently unavailable. Either the Microsoft Exchange Server Computer
	  servicing this public folder is down or the public folder has not been
	  replicated to this site. See your administrator.
	
	RESOLUTION
	==========
	
	To resolve this problem, you need to create a replica of this public folder on
	your server after the Pub.edb restoration process:
	
	1. On the File menu, click Properties.
	
	2. On the public folder, select the instance property and create a replica of
	  that folder on your server.
	
	MORE INFORMATION
	================
	
	The following information from the Microsoft Exchange Disaster Recovery white
	paper by Joseph Pagano relates to the same recovery process.
	
	Restore/Recover the Public Information Store (Pub.edb)
	------------------------------------------------------
	
	1. Prepare a recovery computer.
	
	  a. This computer has to be installed as a Windows NT PDC. The server should
	     have the respective Windows NT service pack installed as the original
	     computer. Confirm that there is enough disk space for restoring the entire
	     information store from your backup tape. Run User manager for Domains and
	     create an account for the Exchange Service Account.
	
	  b. Log on to Windows NT as administrator and install Microsoft Exchange
	     (Complete Install) using the same Site and Organization name that was used
	     on the server in which you are restoring the public folders from. DO NOT
	     JOIN SITE. Note that the server name of the restore computer does not
	     matter for the Public Folder restore procedure. This is because we are
	     only restoring the IS and not the directory.
	
	  c. Install the Microsoft Exchange Client on the Recovery Server.
	
	2. Restore the Information Store from tape.
	
	  This procedure assumes that an off-line tape is used. Make sure the DS is
	  started, then execute the command "isinteg -patch". Start the DS and IS
	  services and then perform the DS/IS Consistency Adjustment.
	
	  a. Run Control Panel Services and stop the following services:
	
	  Microsoft Exchange Message Transfer Agent (MTA).
	  Microsoft Exchange Information Store (IS).
	
	  b. Insert the backup tape in the drive.
	
	  c. Log on to the recovery domain as administrator.
	
	  d. From the Administrative Tools group run BACKUP.
	
	  e. Select the tapes icon and double click on the tape name. A catalog status
	     box will be displayed stating loading.
	
	  f. Select the RESTORE BUTTON from the upper part of the Backup main screen.
	
	  g. On the RESTORE INFORMATION screen enter the directory MDBDATA (where is
	     Pub.edb is located).
	
	  h. From the exchsrvr \ bin directory run the following command:
	
	  ISINTEG -Patch
	
	  i. From Control Panel Services and start the following services:
	
	  Microsoft Exchange Information Store
	  Microsoft Exchange Message Transfer Agent
	
	  j. Run Exchange Admin and perform a DS/IS Consistency Adjustment.
	
	3. Open the contents of a public folder.
	
	  a. Create a profile for the Exchange service account.
	
	  b. After restoring the public folders there are "instance on the site of this
	     folder" but NOT on your server (for the moment). That is the cause of the
	     error message reported in the symptoms section and the reason why you
	     can't access the contents of all the restored folders. To solve this
	     problem you need to select the Public Information Store Object. On the
	     File menu, click Properties and in the "Instance" tab add all the restored
	     folders to your server.
	
	  c. Run the Exchange client using the previous profile and check the entire
	     public folder contents.
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : winnt:5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
