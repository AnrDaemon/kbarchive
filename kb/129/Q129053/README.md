---
layout: page
title: "Q129053: Enabling TCP/IP WinSock Support for RemoteBoot Workstations"
permalink: /kb/129/Q129053/
---

## Q129053: Enabling TCP/IP WinSock Support for RemoteBoot Workstations

{% raw %}

	Article: Q129053
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In order to run non-Microsoft 16-bit Windows Sockets (WinSock) applications on
	RemoteBoot MS-DOS workstations, you must enable WinSock support. This article
	lists a method of enabling WinSock support for RemoteBoot operation using the
	16-bit real mode TCP/IP stack.
	
	MORE INFORMATION
	================
	
	For WinSock support in RemoteBoot operation, do the following:
	
	1. Ensure that the following lines are present in the AUTOEXEC.BAT file located
	  in the %SystemRoot%\RPL\RPLFILES\<profile name> directory:
	
	  UMB.COM
	  LOAD TCPIP
	  NMTSR.EXE
	  SOCKETS.EXE
	
	2. Ensure the following is included in the PATH statement:
	
	  C:\LANMAN.DOS\DRIVERS\PROTOCOL\TCPIP
	
	3. Ensure that following lines are present in the DOSBB.CNF file located in the
	  %SystemRoot%\RPL\BBLOCK\NETBEUI\<adapter name> directory:
	
	  EXE BBLOCK\RPLBIND1.EXE ... TCPDRV.DOS
	
	  NOTE: If any changes are made to the network card configuration details, make
	  the appropriate changes to the PROTOCOL.INI file in the
	  %SystemRoot%\RPL\BBLOCK\NETBEUI\<adapter name> directory.
	
	4. Add the following line to the [tcpglobal] section of the TCPUTILS.INI file
	  located in the %SystemRoot%\RPL\RPLFILES\MACHINES\<machine name>
	  \<profile name>\WKSTA directory:
	
	  [tcpglobal]
	  hostname = <your computer name>
	
	5. Add the following section to the TCPUTILS.INI file located at the
	  %SystemRoot%\RPL\RPLFILES\MACHINES\<machine name>\<profile
	  name>\WKSTA directory:
	
	  [DNR]
	  drivername=DNR$
	  bindings=TCPIP_XIF
	  domain=<TCP/IP domain name>
	  nameserver0=<address of nameserver, separated by spaces>
	
	  NOTE: Changes made to the TCPUTILS.INI file affects only the individual user
	  profile. If the nameserver begins with a numeric digit, add quotes to the
	  entry.
	
	6. Add the following line to the [machinewritable files] section of the
	  DOS622.FIT file located in the %SYSTEMROOT%\RPL\RPLFILES\RPLFIT directory:
	
	  C:\LANMAN.DOS\TCPUTILS.INI\ MACHINES\(cname)\(profile) \WKSTA\TCPUTILS.INI
	
	  NOTE: This line indicates that the TCPUTILS.INI file to be used is located at
	  the individual user's profile directory instead of the global file.
	
	Additional query words: prodnt rpl
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	
	=============================================================================
	

{% endraw %}
