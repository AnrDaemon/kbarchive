---
layout: page
title: "Q189595: PPTP Performance &amp; Security Upgrade for WinNT 4.0 Release Notes"
permalink: /kb/189/Q189595/
---

## Q189595: PPTP Performance &amp; Security Upgrade for WinNT 4.0 Release Notes

{% raw %}

	Article: Q189595
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbfile kbWinNT400sp4fix
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the Point to Point Tunneling Protocol (PPTP)
	Performance Update for Microsoft Windows NT Server and Workstation version 4.0
	Release Notes. For your convenience, the English version of this post-SP3 hotfix
	has been posted to the following Internet location. However, Microsoft
	recommends that you install Windows NT 4.0 Service Pack 4 to correct this
	problem.
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/nt40/hotfixes-postSP3/pptp3-fix/
	
	US and Canadian customers can download the 128-bit version of this hotfix from
	the following web page:
	
	  http://support.microsoft.com/support/ntserver/128Eula.asp
	
	MORE INFORMATION
	================
	
	Point to Point Tunneling Protocol (PPTP) Performance & Security Upgrade
	    for Microsoft Windows NT 4.0 Server and Workstation Release Notes:
	
	Please use this document to address questions that may arise during the
	installation of this PPTP Performance & Security Upgrade for Microsoft
	Windows NT 4.0 Server and Workstation.
	
	---------------------------------------------------------------------
	Contents
	
	- Information on Installation
	
	- Security Features in this Upgrade
	
	- Fixes and Features included from the 2.0 Hotfix
	
	---------------------------------------------------------------------
	
	Information on Installation
	---------------------------
	
	Microsoft has made improvements to the native Virtual Private Networking (VPN)
	capabilities of Windows client and server that significantly improve the
	performance and security PPTP-based VPN connections via the Internet for Windows
	NT Server and Windows NT Workstation version 4.0.
	
	This upgrade should be applied to both Windows NT Servers and Windows NT
	Workstations version 4.0. Service Pack 3 for Windows NT 4.0 must also be
	installed before applying this update.
	
	  Please note: Windows NT Servers running Routing and Remote Access Service
	  (RRAS) must first apply this Windows NT PPTP performance upgrade followed by
	  the RRAS Hotfix 3.0 to benefit from the upgrade (it is important not to
	  reboot your machine in-between installations of the NT PPTP upgrade & the
	  Routing and Remote Access Service upgrade).
	
	For more information, please see the following article in the Microsoft Knowledge
	Base:
	
	  ARTICLE-ID: Q189594
	  TITLE : RRAS Upgrade for WinNT Server 4.0 Hotfix Pack 3.0 Release Notes
	
	This upgrade is packaged in an auto-install format. It is recommended that you
	first copy the upgrade to a temporary directory, and then double-click the
	executable name or type the executable name "pptpfixi.exe" for x86 or
	"pptpfixa.exe" (without the quotation marks) for alpha at a command prompt to
	install.
	
	The files can also be extracted from the Upgrade pack without installing them. To
	do this, copy the Upgrade to a temporary directory, and type "pptpfixi /x" or
	"pptpfixa /x" (without the quotation marks) at a command prompt. After
	extracting the files, the Upgrade can be installed by typing "hotfix" (without
	the quotation marks) at a command prompt.
	
	To uninstall this upgrade, extract the files to a directory using the "/x"
	command as mentioned above and then type "HOTFIX -Y" (without the quotation
	marks) from the same directory you copied the files to.
	
	Output of "HOTFIX -?" :
	
	HOTFIX [-y] [-f] [-n] [-z] [-q] [-m] [-l]
	
	     -y Perform uninstall (only with -m or -q)
	     -f Force apps closed at shutdown
	     -n Do not create uninstall directory
	     -z Do not reboot when update completes
	     -q Quiet Mode -- no user interface
	     -m Unattended mode
	     -l List installed hotfixes
	
	Security Features in this Upgrade
	---------------------------------
	
	This upgrade provides several RAS/PPTP security enhancements for Microsoft
	Windows NT 4.0. This upgrade also includes the performance improvements and
	other fixes that were included in previously released PPTP hotfixes for Windows
	NT Service Pack 3.
	
	- A new version of MSCHAP (MSCHAP V2) has been implemented for VPN connections.
	  This new protocol provides mutual authentication, stronger initial data
	  encryption keys, and different encryption keys for the transmit and receive
	  paths. To minimize the risk of password compromise during MSCHAP exchanges,
	  MSCHAP V2 drops support for the MSCHAP password change V1, and will not
	  transmit the LMHash encoding of the password.
	
	  For VPN connection requests, a Windows NT server will offer MSCHAP V2 before
	  offering the legacy MSCHAP. Updated Windows clients (all platforms) will
	  accept MSCHAP V2 when it is offered. This behavior affects only VPN
	  connections; dial-up connections are not affected.
	
	- A new registry key, SecureVPN, has been defined to force use of MSCHAP V2.
	  When this variable is absent it has a default value of zero. When set to one
	  on a Windows NT server, this registry key causes the server to drop any VPN
	  connections that do not authenticate using MSCHAP V2. This will prevent
	  legacy VPN clients from presenting their credentials in an MSCHAP (or CHAP or
	  PAP) exchange, and is a likely configuration for networks that require a more
	  secure authentication method for VPN connections.
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\RasMan\PPP
	
	  DWORD: SecureVPN
	  Value: 0x00000001 == force MSCHAP V2 for VPN connections
	  Value: 0x00000000 == do not force secure MSCHAP V2 (default)
	
	  When set to one on a Windows NT 4.0 client, the SecureVPN registry key forces
	  the client to use MSCHAP V2 for all VPN (PPTP) connections. Dial-up
	  connections are not affected by this registry setting.
	
	  Please note: Most users will not need to use the Secure VPN flag. This flag
	  should be used with care because it will affect the behavior of all VPN
	  connections from a client. In general, the required use of MSCHAP V2 can be
	  enforced more easily on the server.
	
	- This release also provides a registry variable, UseLmPassword, which can be
	  set to prevent clients from sending the LM response to a legacy MSCHAP
	  challenge or in an MSCHAP change password exchange. When this variable is
	  absent it has a default value of one, allowing use of the LM response (in
	  order to maintain compatibility with legacy systems).
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\RasMan\PPP\Chap
	
	  DWORD: UseLmPassword
	  Value: 0x00000001 == send LMHash of the password (default)
	  Value: 0x00000000 == do not send LMHash of the password
	
	  Setting this variable to zero on a server will cause the server to drop any
	  connection request which uses the LM response in an MSCHAP exchange. Setting
	  this variable to zero on a client will prevent the client from using LM
	  responses in MSCHAP exchanges. This variable affects BOTH dial-up and VPN
	  connections.
	
	  Please note: Most users will not need to use this registry variable. The new
	  secure mode MSCHAP V2 will not send the LMHash response, so this registry
	  value is most useful when connecting to older access servers which use the
	  original MSCHAP.
	
	Fixes and Features included from the 2.0 Hotfix
	-----------------------------------------------
	
	PPTP Performance Issues Addressed in this Update:
	
	- A new historyless mode for encryption & compression over PPTP connections
	  has been enabled. This new mode will dramatically improve performance using
	  PPTP in high latency networks, or networks that commonly experience
	  significant packet loss like the Internet. This upgrade is fully compatible
	  with legacy PPTP systems. However, in order to negotiate historyless mode,
	  both the PPTP client and server must support the upgrade. If either client or
	  server refuses the new mode, normal MPPE compression and encryption will be
	  negotiated to insure communication capabilities are not lost. To experience
	  the full benefit of the PPTP performance update, this update must be
	  installed on both Windows NT clients and servers. A corresponding release
	  Microsoft Dial-Up Networking 1.3 is available for Windows 95 clients, while
	  the new release of Windows 98 already includes the appropriate client code.
	
	  Please note: RAS Servers that terminate compulsory PPTP connections from an
	  FEP (Front End Processor) must disable historyless compression/encryption in
	  order for legacy Windows 95 clients to receive data properly. An FEP is a
	  dial-up server which can create a PPTP tunnel on behalf of its dial-up
	  clients. This feature is available from several Access Server vendors,
	  including Compaq (Microcom), Ascend, and 3com.
	
	  The value to set in the registry to enable/disable historyless
	  encryption/compression is:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NdisWan\Parameters
	
	  DWORD: Historyless
	  Value: 0x00000001 == Enabled (default)
	  Value: 0x00000000 == Disabled
	
	- The default PPTP receive window size was increased to 16.
	
	- The window between the NDISWAN driver and the PPTP driver was increased.
	
	- The PPTP frame size has been set to default to 1400 bytes to avoid packet
	  fragmentation.
	
	  Please note: The frame size issue was also addressed in an earlier hotfix, and
	  is documented at:
	
	  http://support.microsoft.com/support/kb/articles/q162/2/30.asp
	
	Remote Access Service and PPTP Issues:
	
	- PPTP server responsiveness has been improved for the time period right after
	  termination of multiple PPTP connections.
	
	- A PPTP server issue of an improperly configured packet header "start session"
	  has been corrected. This issue is documented at:
	
	  http://support.microsoft.com/support/kb/articles/q179/1/07.asp
	
	- Improved integrity of session encryption in MPPE by increasing the randomness
	  of successive packet key management following an encryption or compression
	  reset.
	
	- Corrected a RAS/PPTP user interface design issue that could mislead an
	  administrator regarding the actual configuration of the server. This issue is
	  documented at:
	
	  http://support.microsoft.com/support/kb/articles/q177/6/70.asp
	
	- Updated MSCHAP to disable sending the LMHash when client set to "require"
	  128-bit encryption.
	
	Other Windows NT Issues Addressed in this Update:
	
	- This release includes an enhancement to TCP/IP which will improve the
	  performance of TCP-based applications over high latency networks, such as the
	  Internet.
	
	Information in this document is subject to change without notice and is provided
	for informational purposes only. The entire risk of the use or results of the
	use of this document remains with the user, and Microsoft Corporation makes no
	warranties, either express or implied. The names of companies, products, people,
	characters, and/or data mentioned herein are fictitious and are in no way
	intended to represent any real individual, company, product, or event, unless
	otherwise noted. Complying with all applicable copyright laws is the
	responsibility of the user. No part of this document may be reproduced or
	transmitted in any form or by any means, electronic or mechanical, for any
	purpose, without the express written permission of Microsoft Corporation.
	
	Microsoft may have patents, patent applications, trademarks, copyrights, or other
	intellectual property rights covering subject matter in this document. Except as
	expressly provided in any written license agreement from Microsoft, the
	furnishing of this document does not give you any license to these patents,
	trademarks, copyrights, or other intellectual property.
	
	(c) 1998 Microsoft Corporation. All rights reserved.
	
	Microsoft, MS-DOS, MS, Windows, Windows NT, are either registered trademarks or
	trademarks of Microsoft Corporation in the U.S.A. and/or other countries.
	
	Other product and company names mentioned herein may be the trademarks of their
	respective owners.
	
	Additional query words: RRAS steel head steelhead ntrouter
	
	======================================================================
	Keywords          : kbfile kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
