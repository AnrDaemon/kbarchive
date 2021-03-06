---
layout: page
title: "Q128459: Capture Does Not Work With HP 10/100 VG ISA NIC"
permalink: /kb/128/Q128459/
---

## Q128459: Capture Does Not Work With HP 10/100 VG ISA NIC

{% raw %}

	Article: Q128459
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.5 
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use HP 10/100 VG ANYLAN network interface card (NIC) with the
	corresponding Windows NT driver (HP J2573A ISA), Network Monitor goes into an
	unusable state (and won't shut down) when you attempt to start a capture.
	
	CAUSE
	=====
	
	This problem occus when Network Monitor makes statistic queries.
	
	WORKAROUND
	==========
	
	HP will soon be releasing a new version of this driver. You can work around this
	problem by using a beta version of this driver (available from the HP Internet
	FTP site).
	
	The driver (HPFEND.SYS) supports ISA, EISA, and PCI VG cards. There are different
	OEMSETUP.INF and .DLL files for each card type.
	
	To use the beta driver:
	
	1. Get J2585A.EXE from the HP FTP site:
	
	  ftp ftp-boi.external.hp.com (192.6.71.2)
	  User: anonymous
	  Password: email-address
	  pub/computer_products/network directory
	  binary
	
	2. Locate the HP VG ISA Support Disk (A.00.03) or download J2573A.EXE from the
	  HP FTP site.
	
	3. Format a floppy disk.
	
	4. Copy the contents of the \WINNT directory from the HP VG ISA disk to the root
	  of the newly formatted floppy disk. Also, copy the file \DISK1 from the HP VG
	  ISA disk to the root of the new floppy.
	
	5. Extract HP VG PCI drivers disk archive (J2585A.EXE) to hard disk.
	
	6. Overwrite \HPFEND.SYS on the new floppy with \BETA\HPFEND.SYS from the HP VG
	  PCI archive.
	
	7. On the Windows NT computer, remove the old ISA driver and then install the
	  new driver from the floppy disk.
	
	
	Additional query words: prodnt
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	
	=============================================================================
	

{% endraw %}
