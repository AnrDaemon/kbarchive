---
layout: page
title: "Q99885: Security Issues Occur Due to How WinNT Handles FPNWCLNT.DLL"
permalink: /kb/099/Q99885/
---

## Q99885: Security Issues Occur Due to How WinNT Handles FPNWCLNT.DLL

{% raw %}

	Article: Q99885
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft File and Print Services for NetWare version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the Restoring
	the Registry online Help topic in Regedit.exe or the Restoring a Registry
	Key online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	The following security issues may arise due to the way Windows NT handles
	Fpnwclnt.dll:
	
	- Windows NT Workstation Setup does not install Fpnwclnt.dll. By default, the
	  NTFS permission on the %SystemRoot%\System32 folder allows Everyone to create
	  new files. This means that anyone who is logged on locally or who has write
	  access to a write-permissible share that includes the %SystemRoot%\System32
	  folder can place a "Trojan horse" version of Fpnwclnt.dll in the System32
	  folder. This version can intercept all passwords changed in the local
	  computer's security account manager (SAM) database. If the computer is a
	  member of a domain, changes to domain user account passwords are not trapped
	  by the password filter.
	
	- Windows NT Server Setup installs Fpnwclnt.dll in the %SystemRoot%\System32
	  folder. If Fpnwclnt.dll is replaced on the Primary Domain Controller (PDC)
	  with a "Trojan horse" DLL, the "Trojan horse" DLL will receive plain-text
	  access to all password updates for the entire domain. However, by default,
	  only a system administrator has access to logon interactively to the domain
	  controller, and only system administrators have access to default file shares
	  that include the System32 folder. The Fpnwclnt.dll file on Backup Domain
	  Controllers (BDC) is never used because all domain password changes are
	  processed at the PDC.
	
	  NOTE: The default ACL on the System32 folder is that only Administrators can
	  modify files but Everyone can add files.
	
	- Administrators can add their own DLL to the following registry key that can
	  obtain the passwords:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA \Notification
	  Packages
	
	RESOLUTION
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	For information about how to edit the registry, view the Changing Keys And Values
	online Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and Edit Registry Data topics in Regedt32.exe. Note
	that you should back up the registry before you edit it.
	
	Perform the following steps to resolve this problem:
	
	1. Apply the latest Windows NT 4.0 Service Pack to remove the registry key on
	  Windows NT Workstation. For information on obtaining the service pack, query
	  on the following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	2. Install Windows NT on an NTFS volume.
	
	3. Make sure the ACL on the following registry key allows only Administrators
	  and the System write access.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA
	
	4. Make sure all values in the following registry key are for password filter
	  packages that Setup intended to install.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA \Notification
	  Packages
	
	5. If you do not use FPNW or DSMN, go to the following registry key and remove
	  the value FPNWCLNT.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA \Notification
	  Packages
	
	6. If you use FPNW or DSMN, make sure Fpnwclnt.dll in the %SystemRoot%\System32
	  folder is the version that ships with Windows NT 4.0 Service Pack 3
	  (05/01/97, 35,088) and that the NTFS ACL only permits access by
	  administrators and the system.
	
	MORE INFORMATION
	================
	
	Fpnwclnt.dll is a dynamic link library that lets File and Print Services for
	NetWare (FPNW) and Directory Service Manager for NetWare (DSMN) perform password
	synchronization with Novell NetWare servers. Fpnwclnt.dll ships with Windows NT
	Server and is in the following default registry configuration:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA \Notification
	  Packages
	
	Although FPNW or DSMN may not be installed on the PDC, this key exists because
	this is the only place to pick up password change notifications and FPNW must
	pick up these changes.
	
	Additional query words: access control list
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbServicesNetwareSearch kbFPNW400
	Version           : WinNT:4.0
	
	=============================================================================
	

{% endraw %}
