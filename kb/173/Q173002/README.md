---
layout: page
title: "Q173002: ACC: How Replication Manager Determines Base Replica"
permalink: /kb/173/Q173002/
---

## Q173002: ACC: How Replication Manager Determines Base Replica

{% raw %}

	Article: Q173002
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:7.0; :
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access Developer's Toolkit, version 7.0 
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Advanced: Requires expert coding, interoperability, and multiuser skills.
	
	Microsoft Replication Manager is a tool included with the Microsoft Access
	Developer's Toolkit (ADT) for Windows 95, version 7.0, and with Microsoft Office
	97 Developer Edition Tools. An important feature of Microsoft Replication
	Manager is its ability to manage members of a replica set and schedule
	synchronizations between them.
	
	One of the components that Microsoft Replication Manager uses to control
	synchronization is the Synchronizer (formerly known as the Transporter in
	Microsoft Replication Manager 3.0). The Synchronizer is a program that runs in
	the background and allows database changes to be stored in a dropbox folder for
	later synchronization. This is especially useful when you are distributing your
	application to users with portable computers that are not always connected to
	the network.
	
	When initiating synchronization between members of a replica set managed by
	multiple Synchronizers, each Synchronizer selects one replica that sends changes
	to and receives changes from a member of the replica set managed by a different
	Synchronizer. Likewise, when initiating a local synchronization of a replica set
	managed by one Synchronizer, Microsoft Replication Manager selects one replica
	that sends changes to and receives changes from all other replicas in the set.
	This replica is called the "base" or "gateway" replica.
	
	This article discusses how the Synchronizer determines which replica is
	designated as the base replica, and what problems may occur as a result.
	
	NOTE: This article assumes you have previously configured Microsoft Replication
	Manager and are currently managing multiple members of a replica set.
	
	MORE INFORMATION
	================
	
	Each Synchronizer is responsible for determining which one of the members of the
	replica set it is currently managing becomes the base replica. The Synchronizer
	uses the following algorithm to determine which replica becomes the base
	replica:
	
	1. Determine which members of the replica set currently managed by this
	  Synchronizer are still valid (that is, not deleted, renamed, inaccessible,
	  and so on).
	
	2. Exclude any partial replicas in the set. Only full replicas can be base
	  replicas.
	
	3. Of the remaining replicas, select the replica with the lowest Replica ID.
	  This replica becomes the base replica; it is designated to send and receive
	  changes during synchronization.
	
	Determining the Current Base Replica
	------------------------------------
	
	To determine which replica has been designated as the base replica by the
	Synchronizer, follow these steps:
	
	1. Start Microsoft Replication Manager.
	
	2. On the File menu, click Open Replica Set. Select a member of a replica set
	  you have previously managed with Microsoft Replication Manager, and then
	  click OK. (In Microsoft Replication Manager 3.0, select a folder you have
	  previously managed from the Folders list.)
	
	3. Right-click the Synchronizer icon that is managing the replica set, and then
	  click "Synchronize Locally Managed Replicas."
	
	4. After the synchronization is complete, right-click the Synchronizer icon
	  again, and then click "View Synchronizer Log File." (In Microsoft Replication
	  Manager 3.0, point to the View menu, and then click Transporter Log.)
	
	5. Scroll to the end of the text file and look for entries in the log
	  documenting the latest synchronization. These entries should look similar to
	  the following:
	
	  Time = 8/7/97 4:00:05 PM
	  Log Type =  Direct exchange
	  Result = Success
	  Replica = C:\Windows\Replicas\Replica1.mdb
	  ReplicaID = {33F32D42-0F20-11D1-9B50-00AA00B67747}
	  Partner Replica Set Member = C:\WINDOWS\replicas\Replica2.mdb
	  ReplicaID = {03B1A944-0F20-11D1-9B50-00AA00B67747}
	
	  Note the "Replica = " entry. This identifies the base replica of the replica
	  set for this synchronization. In the example in Step 5, the base replica is
	  "C:\Windows\Replicas\Replica1.mdb."
	
	Base Replica Scenario
	---------------------
	
	There are scenarios in which the base replica selected by the Synchronizer could
	cause synchronization to take an extended amount of time and generate unexpected
	network traffic. Consider the following:
	
	You have one replica set with three replicas (R1, R2, and R3), located on three
	computers (Machine A, Machine B, and Machine C). R1 is located on Machine A, R2
	is located on Machine B, and R3 is located on Machine C. All three replicas are
	being managed by a Synchronizer running on Machine A. Machines A and B are both
	located on the same local area network (LAN), while Machine C is located on a
	separate LAN that is accessible over a wide area network (WAN).
	
	Assume that R3 has the lowest Replica ID in this replica set, and that all
	replicas in the set are valid (not deleted, renamed, or inaccessible).
	Synchronizer will select R3 as the base replica. Therefore, when synchronization
	is initiated through Microsoft Replication Manager, R3 will be involved in every
	synchronization to other members of the same replica set managed by this
	Synchronizer. Since R3 is physically located on a remote computer, this may
	cause synchronization to take an extended amount of time and cause an
	unanticipated amount of network traffic. In this scenario, you can improve
	performance and reduce the amount of network traffic by moving R3 to Machine A
	(where its Synchronizer is located) and by moving one of the other replicas to
	Machine C.
	
	Moving a Replica in Microsoft Replication Manager
	-------------------------------------------------
	
	To move a managed replica to another location, follow these steps. If you
	manually move a managed replica instead of following these steps, the replica
	will be marked as invalid, and it will be removed from the list of managed
	replicas.
	
	1. Start Microsoft Replication Manager.
	
	2. On the File menu, click Open Replica Set. Select a member of a replica set
	  you have previously managed with Microsoft Replication Manager, and then
	  click OK. (In Microsoft Replication Manager 3.0, select a folder you have
	  previously managed from the Folders list.)
	
	3. On the File menu, click Move Replica.
	
	4. In the Move Replica dialog box, select the replica you want to move, and then
	  click Open.
	
	5. In the Move To dialog box, select the location you want to move the replica
	  to, and then click Save.
	
	6. Repeat steps 3 through 5 for each replica that you want to move.
	
	REFERENCES
	==========
	
	For more information about Microsoft Replication Manager, please see the
	Microsoft Jet Replication white paper. This white paper is included with
	Microsoft Office 97 Developer Edition Tools. You can also obtain this white
	paper from the Microsoft Download Center on the World Wide Web. For more
	information on how to obtain the Microsoft Jet Replication white paper, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q164553 ACC97: Jet 3.5 Replication White Paper Available in Download Center
	
	Additional query words: hub gateway
	
	======================================================================
	Keywords          :  
	Technology        : kbOfficeSearch kbAudDeveloper kbAccessSearch kbOffice97Search kbOffice97 kbZNotKeyword3 kbAccessDevTK700 kbOffice97DevSearch
	Version           : WINDOWS:7.0; :
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
