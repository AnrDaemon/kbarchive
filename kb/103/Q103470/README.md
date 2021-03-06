---
layout: page
title: "Q103470: NetBIOS Name Conflicts When NetBEUI Used on Multiple NICs"
permalink: /kb/103/Q103470/
---

## Q103470: NetBIOS Name Conflicts When NetBEUI Used on Multiple NICs

{% raw %}

	Article: Q103470
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.1,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can configure multiple network interface cards (NICs, also called network
	adapters) in a computer (multihomed) for use on the same network segment, but no
	two network adapters on the same segment in the computer can use NetBIOS. When
	you install NetBEUI on a multihomed computer, it violates this restriction.
	
	MORE INFORMATION
	================
	
	When you install NetBEUI on a multihomed computer, NetBEUI binds to all
	available network adapters in the computer regardless of whether they are on the
	same physical network segment. If a computer containing two or more network
	adapters uses the same protocol on more than one network adapter in a given
	network segment, the computer sees duplicate computer names due to the resulting
	NetBIOS name conflict, generates an error, and fails to start system services
	correctly. This also occurs if both segments are bridged.
	
	The event log may show an Event ID 2505 error (duplicate name on the network).
	The error may appear in the event log as either of the following messages:
	
	- Event ID : 2505
	  The server could not bind to the transport/device/netbt_<nic driver>
	  because another computer on the network has the same name. The server could
	  not start.
	
	- Event ID : 2505
	  The server could not bind to the transport/device/nbf_<nic driver>
	  because another computer on the network has the same name. The server could
	  not start.
	
	The event log may also show:
	
	- Event ID: 3870
	  Source: workstation <computer name> is not a valid computer name.
	
	This problem does not affect routable protocols (TCP/IP, AppleTalk and NWLink)
	because when you install or reconfigure them you have to choose a network
	adapter in Control Panel's Network configuration window, and this automatically
	disables the protocol's bindings to other adapters. When installing TCP/IP, for
	instance, you are forced to provide unique IP addresses to each network adapter,
	then choose one network adapter as the "Windows Networking Adapter" in the
	"Windows Networking on TCP/IP (NetBIOS)" box of the TCP/IP Configuration
	window.
	
	You can manually configure multiple network adapters in a computer by disabling
	NetBEUI bindings to network adapters other than the one you want to use for the
	NetBEUI protocol. To do this, disable the following bindings:
	
	- Server to NetBEUI protocol to <adapter driver> to <adapter>
	
	- Workstation to NetBEUI protocol to <adapter driver> to <adapter>
	
	- NetBEUI protocol to <adapter driver> to <adapter>
	
	- NetBIOS Interface to NetBEUI protocol to <adapter driver> to
	  <adapter>
	
	When you have disabled all of these bindings, network operations can proceed.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q131736
	  TITLE : TCP/IP: Load Balancing vs. Distributed Network Sessions
	
	Additional query words: duplicate multihomed bridged netbf netbeui event 2504 duplicate name server could not bind 3.10
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : WinNT:3.1,3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
