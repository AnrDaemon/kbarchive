---
layout: page
title: "Q84302: Unable to Get into 386 Enhanced Mode with SCSIDISK.SYS"
permalink: /kb/084/Q84302/
---

## Q84302: Unable to Get into 386 Enhanced Mode with SCSIDISK.SYS

{% raw %}

	Article: Q84302
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	IBM PS/2 computers equipped with the original IBM hard disk and a Procom MC
	Enabler SCSI host adapter may have difficulty running Microsoft Windows version
	3.1 in 386 enhanced mode.
	
	If Windows 3.1 fails to run in 386 enhanced mode only when the device driver
	SCSIDISK.SYS is being loaded, this problem can probably be resolved by disabling
	the MC Enabler SCSI host adapter's direct memory access (DMA) settings.
	
	MORE INFORMATION
	================
	
	According to Procom technical support, the following set of steps should be used
	to reconfigure the PS/2's DMA settings.
	
	1. Restart the computer from the IBM Reference disk. You must use a copy of the
	  Reference disk that contains all of the proper Adapter Descriptor Files (ADF)
	  for your machine. For more information on ADF files, please see the section
	  below "ADF files".
	
	2. From the Set Configuration menu, choose Change Configuration. Note the
	  current settings under DMA Arbitration Level for both the Procom SCSI Enabler
	  and the other hard disk in the system.
	
	3. Swap the levels of both controllers. For example, if the MC Enabler is set to
	  level 5 and the other hard disk in the system is at level 6, make the MC
	  Enabler level 6 and the existing hard disk level 5.
	
	ADF Files
	---------
	
	PS/2 machines come with a write-protected reference disk. In the main menu on
	this disk, you are prompted to make a backup or working copy of the original
	disk. This working copy will be customized for one machine.
	
	Any time you add a new system card, such as the Procom's MC SCSI Enabler, the
	card should come with a disk containing the proper ADF files for that card.
	
	After installing the card you should boot the computer from the backup reference
	disk. One of the options at the menu is to add ADF files to the working copy of
	the IBM reference disk. Select the option to update the ADF files and follow the
	instructions to copy the ADF files from the new disk that came with the card to
	the working copy of the IBM reference disk. This will allow you to properly
	configure the card for that particular machine with the new card installed.
	
	For additional information, please contact Procom Technology technical support.
	
	The Procom product included here is manufactured by a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: 3.10 3.11 3rdparty
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
