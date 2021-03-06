---
layout: page
title: "Q307465: Windows NT 4.0 Cluster Deletes Symbolic Link for Reserved Disks"
permalink: /kb/307/Q307465/
---

## Q307465: Windows NT 4.0 Cluster Deletes Symbolic Link for Reserved Disks

{% raw %}

	Article: Q307465
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP4,4.0 SP5,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbenv w2000mscs
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform a Move Group/Failover procedure in a Windows NT 4.0-based
	cluster, the following error message may be logged in the Cluster log:
	
	  Physical Disk "DRIVELETTER:" DiskspCheckPath: FindFirstFile for
	  "DRIVELETTER:" failed, error 3.
	
	This error message is typically logged when the second cluster of a two-node
	cluster is brought online if the cluster had failback for a cluster group set to
	failback to that node.
	
	You may also receive the following error message when you perform a Move Group
	procedure:
	
	  Physical Disk "DRIVELETTER:" SCSI, error reserving disk, error 21.
	
	CAUSE
	=====
	
	You receive the following error message if you install a regression fix from
	Windows NT 4.0 Service Pack 6a (SP6a):
	
	  Physical Disk "DRIVELETTER:" SCSI, error reserving disk, error 21
	
	Under certain conditions, the cluster disk driver (Clusdisk.sys) attempts to
	attach to devices and does not read a partition table from the devices (assuming
	that they are cluster disks that are reserved by the other node).
	
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to
	computers that are experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information about support costs, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date       Time   Version    Size       File name   
	  ----------------------------------------------------
	  12-Nov-01  21:17  1.0.224.6   29,360    Clusdisk.sys
	  12-Nov-01  21:17  1.0.224.6  169,744    Clusres.dll
	  12-Nov-01  21:17  1.0.224.6   29,968    Resutils.dll
	
	NOTE: Due to file dependencies, this hotfix requires Microsoft Windows NT 4.0
	SP6a.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	Additional query words: mscs 21
	
	======================================================================
	Keywords          : kbenv w2000mscs 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400search kbWinNTSEnt400SP6a
	Version           : :4.0,4.0 SP4,4.0 SP5,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
