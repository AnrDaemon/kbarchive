---
layout: page
title: "Q98460: Using SyQuest Removable Drives and Tape Drives with MS-DOS 6"
permalink: /kb/098/Q98460/
---

## Q98460: Using SyQuest Removable Drives and Tape Drives with MS-DOS 6

{% raw %}

	Article: Q98460
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article covers the use of MS-DOS 6.0 with SyQuest removable-media drives
	and tape drives.
	
	MORE INFORMATION
	================
	
	Using MS-DOS 6.0 on SyQuest Removable-Media Drives
	--------------------------------------------------
	
	MS-DOS 6 Upgrade Setup returns an "Incompatible medium" error message when you
	attempt to install onto a SYDOS removable-media drive.
	
	SyQuest driver versions 2.61 and earlier are incompatible with MS-DOS 6.0.
	SyQuest is aware of this problem and has provided an updated driver contained in
	the self-extracting file DRIVER.EXE. The latest version of the driver is 2.74,
	which is compatible with MS-DOS 6.0.
	
	To obtain DRIVER.EXE, call SyQuest or download it from the SyQuest bulletin board
	service (BBS).
	
	SyQuest recommends loading this driver first in the CONFIG.SYS file. It should
	always be loaded before the DEVICEHIGH=C:\DOS\DBLSPACE.SYS /MOVE line.
	
	NOTE: SyQuest recommends that you do not use any disk caches (including
	SMARTDrive) with SyQuest disk drives because they do not provide proper support
	for caching.
	
	Using SyQuest Tape Drives with MS-DOS 6
	---------------------------------------
	
	According to SyQuest Technical Support, the SyQuest tape drive device driver
	SQ55.SYS dated July 1990 is incompatible with MS-DOS 6.0.
	
	To work around this problem, obtain an updated device driver from SyQuest.
	SyQuest removable tape drives require the SQ55.SYS device driver.
	
	
	REFERENCES
	==========
	
	The SYDOS product included here is manufactured by SyQuest Corporation, a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	this product's performance or reliability.
	
	For more information, contact SyQuest Technical Support.
	
	Additional query words: 6.00 removable SY SQ smart drive smartdrv.exe cache read write
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS600
	Version           : MS-DOS:6.0
	
	=============================================================================
	

{% endraw %}
