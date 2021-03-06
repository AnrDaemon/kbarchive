---
layout: page
title: "Q158866: How to Manually Create an Emergency Repair Disk"
permalink: /kb/158/Q158866/
---

## Q158866: How to Manually Create an Emergency Repair Disk

{% raw %}

	Article: Q158866
	Product(s): Microsoft Windows NT
	Version(s): 2000,3.51,4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 12-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Advanced Server 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	When you try to run an emergency repair, and you do not have an emergency repair
	disk, the emergency repair fails when you use the files located in the
	\%Systemroot%\Repair folder.
	
	MORE INFORMATION
	================
	
	If the Windows NT system files are on a file allocation table (FAT) partition,
	or a partition formatted with MS-DOS, and you cannot start Windows NT, start to
	MS-DOS by either selecting MS-DOS from the menu or from an MS-DOS startup floppy
	disk. Copy the contents of the \%Systemroot%\Repair folder to the root of a
	Windows NT formatted floppy disk.
	
	NOTE: If creating an Emergency Repair disk booted via DOS from a FAT partitioin
	then ensure that the System, Hidden, and Read-Only file attributes are removed
	from the Setup.log file in the %SYSTEMROOT/REPAIR folder. This ensures that the
	Setup.log file is copied onto the diskette.
	
	If the Windows NT system files are on an NTFS file system partition, install
	another copy of Windows NT into a separate and unique directory. Start Windows
	NT from this install. Copy the contents of the \%Systemroot%\Repair folder to
	the root of a Windows NT formatted floppy disk. Alternately, if you have a
	backup tape from the failed system, you can restore the %Systemroot%\Repair
	folder and copy the restored files to the root of the formatted floppy disk.
	
	To create a Windows NT formatted floppy disk on Windows NT 3.51, double- click on
	the File Manager icon, place a floppy disk in the floppy disk drive, click the
	Disk menu, and click Format Disk. The Format Disk dialog appears. Select the
	drive and capacity, and then click OK.
	
	To format a floppy disk, from the Desktop, double-click My Computer. Place a
	floppy disk in the floppy disk drive. Right-click the disk drive icon. Click
	Format, and then click OK.
	
	You can now run the repair process. Select "Emergency Repair Disk," and insert
	the disk you just created.
	
	Additional query words: Emergency Repair Disk prodnt 4.0
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbWinNTS351search kbWinAdvServSearch
	Version           : :2000,3.51,4.0
	
	=============================================================================
	

{% endraw %}
