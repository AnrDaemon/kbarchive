---
layout: page
title: "Q35766: Supported Values for FORMAT /N and /T Switches"
permalink: /kb/035/Q35766/
---

## Q35766: Supported Values for FORMAT /N and /T Switches

{% raw %}

	Article: Q35766
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The FORMAT.COM utility supports two new switches, /N and /T. The /N switch
	allows you to specify the number of tracks on the disk to be formatted.
	Similarly, the /T switch allows you to specify the number of sectors per track
	on the disk to be formatted. You must use the /T and /N switches together; you
	cannot use them separately.
	
	These are "open-ended" switches. That is, they do not work for all values, only
	values that are supported by the ROM BIOS of your system. Specifying a value
	that is not supported by the ROM BIOS results in the FORMAT.COM utility
	returning the error "parameters not supported."
	
	Additional query words: 6.22 3.20 3.21 3.30 3.30a 4.00 5.00 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.0,5.0a,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
