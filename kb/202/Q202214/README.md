---
layout: page
title: "Q202214: Err Msg: &quot;HAL: No MPS Table Found&quot; During Restart"
permalink: /kb/202/Q202214/
---

## Q202214: Err Msg: &quot;HAL: No MPS Table Found&quot; During Restart

{% raw %}

	Article: Q202214
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51,4.0,4.0a
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 20-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Cluster Server, included with:
	   - Microsoft BackOffice Server 4.0 
	   - Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	   - Microsoft BackOffice Small Business Server versions 4.0, 4.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If your computer normally reports two system processors while running Windows NT
	and one processor fails, your computer may stop responding. When you attempt to
	restart the server into Windows NT you may receive the following error message
	on a blue screen:
	
	  HAL: MPS MP Structure not found HAL: No MPS table found
	
	  HAL: This Hal.dll requires an MPS version 1.1 system. Replace Hal.dll with the
	  correct HAL for this system. The system is halting.
	
	If your computer is a Compaq SystemPro compatible system, the following error
	message may be displayed:
	
	  HAL: Systempro Hal.dll cannot be run on non Systempro compatible Replace the
	  Hal.dll with the correct HAL for this system. The System is halting.
	
	CAUSE
	=====
	
	This behavior occurs when the APIC tables are not available for use by the
	multiprocessor hardware abstraction layer (HAL).
	
	The HAL looks for APIC tables enabled in the system firmware/BIOS. These tables
	are enabled only if both processors are installed and recognized by the system
	firmware/BIOS during power-on self test (POST).
	
	RESOLUTION
	==========
	
	Until the hardware or processor can be repaired or replaced, use the
	uniprocessor kernel and HAL files to get the system back into production. To do
	this, use the appropriate method.
	
	NOTE: If your system has a service pack installed, you must use the Ntoskrnl.exe
	and Hal.dll files from the same service pack version as that of the computer you
	are attempting to repair.
	
	If the Windows NT System Files are on a FAT Partition
	-----------------------------------------------------
	
	1. Start the computer using an MS-DOS disk.
	
	2. Copy the regular uniprocessor versions of the Ntoskrnl.exe and Hall.dll files
	  from the Windows NT CD-ROM (or service pack source folder) to the
	  %SystemRoot%\System32 folder, and rename the files to Ntkrnlsp.exe and
	  Halsp.dll, respectively. For example, type the following commands:
	
	   - copy d:\i386\ntoskrnl.exe c:\winnt\system32\ntkrnlsp.exe
	
	   - copy d:\i386\hal.dll c:\winnt\system32\halsp.dll
	
	3. Modify the Boot.ini file and make a new entry as follows:
	
	multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows NT Server Version 4.00 [Uni-processor]" /kernel=ntkrnlsp.exe /hal=halsp.dll
	
	4. Restart the server and select the new [Uni-Processor] option from the Boot
	  menu. Choosing this option loads the uniprocessor files Ntkrnlsp.exe and
	  Halsp.dll (instead of the normal multiprocessor files) so that you can
	  restart the computer and log on.
	
	After you fix the processor or hardware problem, restart using the normal Boot
	menu option. You should once again be up on multiprocessor support.
	
	NOTE: If you want the [Uni-processor] boot entry to remain compatible after you
	install service packs in the future, you must manually update the Ntkrnlsp.exe
	and Halsp.dll files with the version included in the newer service pack.
	
	If the Windows NT System Files Are on an NTFS Partition
	-------------------------------------------------------
	
	Use the Emergency Repair Disk (ERD) to install the uniprocessor HAL and kernel
	files on the system using the steps outlined below. For further information, you
	can refer to the following article in the Microsoft Knowledge Base:
	
	  Q164471 Replacing System Files Using a Modified Emergency Repair Disk
	
	1. Make a backup copy of the Setup.log file located on the ERD. Modify the
	  original file by adding two entries in the [Files.WinNt] section as shown in
	  the following example:
	
	[Paths]
	TargetDirectory = "\WINNT"
	TargetDevice = "\Device\Harddisk0\partition1"
	SystemPartitionDirectory = "\"
	SystemPartition = "\Device\Harddisk0\partition1"
	[Signature]
	Version = "WinNt4.0"
	[Files.SystemPartition]
	ntldr = "ntldr","2a36b"
	NTDETECT.COM = "NTDETECT.COM","b69e"
	[Files.WinNt]
	\WINNT\system32\ntoskrnl.exe = "ntoskrnl.exe","99999","\","source disk","ntoskrnl.exe"
	\WINNT\system32\hal.dll = "hal.dll","99999","\","source disk","hal.dll"
	
	2. Place the uniprocessor version of the Ntoskrnl.exe and Hal.dll files from the
	  service pack or Windows NT installation CD-ROM on a separate disk.
	
	3. If you are repairing a Windows NT 4.0 system, replace the Setupdd.sys file
	  from Windows NT 4.0 Service Pack 2 or later on Setup Disk 2, as described in
	  the following article in the Microsoft Knowledge Base:
	
	  Q168015: Files Not Replaced When Running Emergency Repair on X86 Intel
	
	4. Boot from the three Setup disks. Click R to repair, and then click the
	  "Verify Windows NT system files" option.
	
	5. After you replace the kernel and HAL files, press F3 to quit the repair
	  process (do not let the repair process replace any other files).
	
	6. Restart the server. The uniprocessor kernel and HAL files should be loaded,
	  and you should be able to log on.
	
	7. After you log on, create a Boot.ini entry to select a [Uni-processor]
	  environment to ensure that you can log on to Windows NT easily in the event
	  of another processor failure.
	
	8. Make a copy the uniprocessor versions of the Ntoskrnl.exe and Hal.dll files
	  located in the %SystemRoot%\System32 folder, and rename them to Ntkrnlsp.exe
	  and Halsp.dll, respectively. For example, type the following commands:
	
	   - copy c:\winnt\system32\ntoskrnl.exe c:\winnt\system32\ntkrnlsp.exe
	
	   - copy c:\winnt\system32\hal.dll c:\winnt\system32\halsp.dll
	
	9. Modify the Boot.ini file and create a new entry as follows:
	
	multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows NT Server Version 4.00 [Uni-processor]" /hal=halsp.dll /kernel=ntkrnlsp.exe
	
	10. Restart the server and select the new {Uni-Processor] option from the Boot
	  menu. Choosing this option loads the uniprocessor files Ntkrnlsp.exe and
	  Halsp.dll (instead of the normal multiprocessor files) and then you can log
	  on.
	
	11. After you fix the processor or hardware problem, copy the multiprocessor
	  version of the Ntkrnlmp.exe and Halmps.dll files from the Windows NT
	  installation CD-ROM (or service pack) to the %SystemRoot%\System32 folder,
	  and then restart the computer. For example, type the following commands:
	
	   - copy d:\i386\ntkrnlmp.exe c:\winnt\system32\ntoskrnl.exe
	
	   - copy d:\i386\halmps.dll c:\winnt\system32\hal.dll
	
	You should be up on multiprocessor support, but a Boot menu choice to use
	uniprocessor support is now available.
	
	Additional query words: kbDSupport
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbAudDeveloper kbClustServSearch
	Version           : winnt:3.5,3.51,4.0,4.0a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
