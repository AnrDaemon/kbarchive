---
layout: page
title: "Q120752: How to Diagnose Event ID 4320 or 4319"
permalink: /kb/120/Q120752/
---

## Q120752: How to Diagnose Event ID 4320 or 4319

{% raw %}

	Article: Q120752
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On your Windows NT-based computer, you may receive one of the following event
	log messages in Event Viewer:
	
	  Event ID: 4320
	  Source: NetBT
	  Type: Error
	  Description: Another machine has sent a name release message to this machine
	  probably because a duplicate name has been detected on the TCP network. The
	  IP address of the node that sent the message is in the data. Use nbtstat -n
	  in a command window to see which name is in the Conflict state.
	
	  -or-
	
	  Event ID: 4319
	  Source: NetBT
	  Type: Error
	  Description: A duplicate name has been detected on the TCP network. The IP
	  address of the machine that sent the message is in the data. Use nbtstat -n
	  in a command window to check which name is in the conflict state.
	
	CAUSE
	=====
	
	This message is caused when another computer sends a name release message to
	your computer. The most likely reason for this is that a duplicate name has been
	detected on the network.
	
	
	MORE INFORMATION
	================
	
	Use the NBTSTAT -N command to see the name of the computer in the conflict
	state. The IP address of the node that sent the message is in the data returned
	by this command. The following example shows what the data may look like in one
	of these events:
	
	  0000:   00   00   04   00   01   00   54   00
	  0008:   00   00   00   00   e0   10   00   c0
	  0010:   00   00   00   00   00   00   00   00
	  0018:   00   00   00   00   00   00   00   00
	  0020:   00   00   00   00   00   00   00   00
	  0028:   e7   1a   65   16
	
	Offset 28 is the IP address of the computer requesting name release. To determine
	the decimal IP address, invert the four hexadecimal numbers and convert them to
	decimal numbers separated by periods. Using this method, the IP address of E7 1A
	65 16 becomes 22.101.26.231.
	
	The status column of the NBTSTAT output for the computer in conflict should
	contain either "Conflict" or "Released."
	
	You can run the NBTSTAT -A command with the IP address to get the computer name.
	
	NOTE: This error message is generated in many cases due to normal circumstances,
	and should not be cause for alarm.
	
	Additional query words: prodnt WINS Conflict
	
	======================================================================
	Keywords          : kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : winnt:3.5,3.51,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
