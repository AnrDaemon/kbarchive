---
layout: page
title: "Q99592: Three Conditions Affecting Maynstream OS/2 Software"
permalink: /kb/099/Q99592/
---

## Q99592: Three Conditions Affecting Maynstream OS/2 Software

{% raw %}

	Article: Q99592
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	When you install Maynard Maynstream OS/2 software on a LAN Manager 2.1 server,
	several conditions arising during file system backup can affect operation and
	performance. This article discusses three reported conditions and how to avoid
	or alleviate them.
	
	Systems on which these conditions have been observed consisted of:
	
	- Gateway 2000 486DX2/50 EISA machine with an Adaptec 174x controller running
	  in enhanced mode
	
	- MicroNet 2 GB hard disk
	
	- Maynstream 16-bit ISA SCSI board
	
	- Maynard 5000 5 MB tape backup system
	
	- LAN Manager 2.1 server running HPFS386 on all volumes
	
	MORE INFORMATION
	================
	
	Condition 1
	-----------
	
	The Maynard software reports that it cannot open certain files scattered
	throughout a directory tree's subdirectories. Sometimes files that are
	completely accessible from an OS/2 command prompt and that have extended
	attributes (EAs) and permissions are set correctly do not get backed because an
	MS-DOS/Windows machine does not understand an extended attribute and does not
	read it across the net. So new EAs are created as the files are moved back to
	the OS/2 server.
	
	Resolution: Use an MS-DOS or Windows workstation to copy all of the files to
	another place on the same disk that stripped the EAs.
	
	Condition 2
	-----------
	
	A number of files are reported "Not Found on the hard drive" during the backup
	verify phase. The path attached to the files is not correct, or for some reason
	the Maynstream software is not reading the directories and paths properly when
	it writes the files to tape.
	
	Resolution: Create new directories, copy all files into them, then delete the old
	ones.
	
	Condition 3
	-----------
	
	While a backup or restore is running on the tape backup system, all workstations
	suffer a significant performance loss. Windows freezes for numerous seconds on
	all of the WFWG RC2 workstations, preventing logon to the server.
	
	Resolution: Maynstream OS/2 uses any resources it can find, including CPU time,
	but if you switch to another screen whenever it is accessing the tape drive,
	workstation performance is restored.
	
	Additional query words: 2.00 2.0 2.10 2.1 2.10a 2.1a 2.20 2.2
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
