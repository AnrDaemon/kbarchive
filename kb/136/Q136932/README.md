---
layout: page
title: "Q136932: SMS Fails to Upgrade MS-DOS and Windows on NetWare Clients"
permalink: /kb/136/Q136932/
---

## Q136932: SMS Fails to Upgrade MS-DOS and Windows on NetWare Clients

{% raw %}

	Article: Q136932
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1
	Operating System(s): 
	Keyword(s): kbnetwork kbsmsUtil smsutil
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	When you use Systems Management Server to perform MS-DOS or Windows upgrades of
	Novell NetWare clients with the included package definition files (PDFs), the
	following error message appears when the client attempts to execute the
	package:
	
	  Invalid Drive Specification
	
	CAUSE
	=====
	
	Your NetWare client has lost its network connection to your Systems Management
	Server distribution server and, therefore, cannot find the WINSTART.EXE,
	UPGRD622.EXE and STPUP622.EXE Systems Management Server utilities located in the
	MSTEST directory of the Systems Management Server logon server.
	
	During the upgrade procedure but before SETUP.EXE starts on the NetWare client
	the network functionality is lost and thus the connection to the Systems
	Management Server distribution server is disconnected. When later during the
	upgrade procedure Setup starts on the NetWare client and attempts to use the
	previous drive specification to connect to the Systems Management Server, it
	fails and displays the above error message.
	
	This problem occurs only with NetWare clients using NETX and VLM drivers, because
	these network drive connections made under Windows are disconnected when Windows
	is quit during the upgrade procedure.
	
	For more details, please read the MORE INFORMATION section below.
	
	WORKAROUND
	==========
	
	To work around this problem, modify the PDF to use the undocumented /LOCAL
	switch with the WINSTART.EXE, UPGRD622.EXE, and STPUP622.EXE Systems Management
	Server utilities.
	
	The /LOCAL switch causes the package distribution to be copied to a temporary
	directory on the NetWare client, before SETUP.EXE starts on the NetWare client.
	When Setup starts, it finds the files in the local temporary directory and
	therefore does not need a network connection to the distribution server.
	
	NOTE: This workaround temporarily requires additional hard disk space on the
	NetWare client for the files in the temporary directory. This directory is
	automatically deleted after the upgrade.
	
	Modifying the PDF
	-----------------
	
	You can apply the /LOCAL switch to the PDF directly by editing the PDF in a text
	editor. This causes future package creations using this PDF to include the
	/LOCAL switch. You can also apply the /LOCAL switch by using Systems Management
	Server Administrator as follows:
	
	To modify DOS622.PDF and WFW311.PDF to use the /LOCAL switch:
	
	1. In Systems Management Server Administrator, select your existing package for
	  MS-DOS 6.22 or Windows for Workgroups 3.11 from the packages window.
	
	2. Choose Workstations from the Package Properties dialog.
	
	3. Choose Properties for the type of install/upgrade.
	
	4. If the command line begins with UPGRD622, STPUP622, or WINSTART, insert
	  /LOCAL between the command and its parameters. Leave a space between the
	  command and /LOCAL. For a Batch Step-Up Win/WfW Client, the modified command
	  line should appear as follows:
	
	     stpup622 /LOCAL setup.exe /H /G /U
	
	5. Choose Close and then OK to save the package definition.
	
	If the package has already been distributed and failed due to the above cause,
	you do not need to redistribute the entire package again. Resend the new
	instruction to the clients without refreshing existing distribution servers.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.00 and 1.10. This problem has been corrected in the latest U.S.
	Service Pack for Systems Management Server version 1.10. For information on
	obtaining the Service Pack, query on the following word in the Microsoft Kn
	wledge Base:
	
	  " SERVPACK " (without the quotation marks)
	
	
	MORE INFORMATION
	================
	
	The MS-DOS based SETUP.EXE programs for both MS-DOS and Windows upgrades attempt
	to detect Windows when they are started and quit if they detect that Windows is
	running. Using the UPGRD622.EXE, STPUP622.EXE, and WINSTART.EXE utilities,
	Windows minimizes its memory usage using the ExitWinExec application programming
	interface (API) to execute another Systems Management Server utility,
	OUTSMART.EXE that in turn is passed a parameter naming another program, usually
	SETUP.EXE. OUTSMART.EXE literally 'outsmarts' SETUP.EXE or the passed program
	into believing there is no running instance of Windows.
	
	The WINSTART.EXE, UPGRD622.EXE and STPUP622.EXE utilities all build paths to
	OUTSMART.EXE located on the logon server using universal naming convention (UNC)
	names and a drive connection to the distribution server using a drive letter.
	Therefore, an example of the intended command line passed to the ExitWinExec API
	is:
	
	\\LOGONSRVR\MSTEST\OUTSMART X:\SMS\PCM_PKG.SRC\PKGID\SETUP.EXE /H /G /U
	
	On a NetWare client, the connection Package Command Manager (PCM) makes to the
	distribution server is lost during execution of ExitWinExec causing OUTSMART to
	lose the path to SETUP.EXE. Therefore, the three Systems Management Server
	utilities were modified to accept the /LOCAL switch to allow the package
	distribution to be copied to the NetWare client.
	
	Additional query words: prodsms sms
	
	======================================================================
	Keywords          : kbnetwork kbsmsUtil smsutil 
	Technology        : kbSMSSearch kbSMS100 kbSMS110
	Version           : winnt:1.0,1.1
	
	=============================================================================
	

{% endraw %}
