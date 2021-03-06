---
layout: page
title: "Q175275: How to Replace Shared SCSI Controller When Using MSCS"
permalink: /kb/175/Q175275/
---

## Q175275: How to Replace Shared SCSI Controller When Using MSCS

{% raw %}

	Article: Q175275
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Cluster Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If one of the controllers on a shared SCSI bus fails while using Microsoft
	Cluster Server, simply power off that node and replace the controller with one
	of the same make, model, and firmware version.
	
	MORE INFORMATION
	================
	
	There are many ways a SCSI controller can fail. Typical signs of imminent SCSI
	controller failure can be seen by monitoring the System Event Log for Event ID:
	11 and Event ID: 9.
	
	For additional information on these events, please see the following articles in
	the Microsoft Knowledge Base:
	
	ARTICLE-ID: Q153128
	TITLE : Event IDs 9 and 11: SCSI Controller/Device Errors
	
	ARTICLE-ID: Q154690
	TITLE : How to Troubleshoot Event 9 and Event 11 Error Messages
	
	When you replace the failed SCSI controller, make sure the new controller has the
	same firmware as the working controller in the other node.
	
	Follow these steps to replace the failed or failing SCSI controller:
	
	1. Power off the node with failed or failing adapter. If possible, manually move
	  all groups to another node using Cluster Administrator.
	
	2. Verify that all groups and resources are online on the functioning node.
	
	3. Remove and replace SCSI controller in failed node.
	
	4. Power on the node and log on normally.
	
	5. Check the event log for any unusual errors.
	
	6. Start Cluster Administrator and verify groups and resources are online and
	  have failed back if so configured.
	
	NOTE: After replacing the controller, set the SCSI ID for the new controller to
	be the same as the old one. Microsoft Cluster Server should start and function
	normally. If your configuration does not use SCSI Y cables or specialized
	cables, you may have to shut down both nodes. SCSI Y cables allow termination of
	the bus regardless of connection to the controller. With standard SCSI cables,
	termination may be lost when you disconnect the faulty controller.
	
	You may have successfully repaired the problem if:
	
	- There are no unusual event messages in the event viewer.
	
	- Cluster Administrator starts and allows you to view the cluster.
	
	- Groups and resources may be moved successfully to the node with the new
	  controller.
	
	Additional query words: MSCS
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbAudDeveloper kbClustServSearch
	Version           : WinNT:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
