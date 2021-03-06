---
layout: page
title: "Q197294: DNS May Return Wrong IP Address When Forwarding Query to WINS"
permalink: /kb/197/Q197294/
---

## Q197294: DNS May Return Wrong IP Address When Forwarding Query to WINS

{% raw %}

	Article: Q197294
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a client queries the Microsoft DNS server for an IP address, and the DNS
	forwards the query to WINS, if the WINS server is busy, the DNS server may
	return the IP address for a different name. This will happen on an intermittent
	basis randomly.
	
	CAUSE
	=====
	
	When the DNS sends a query to WINS, it includes a transaction ID (XID) so that
	it can match up responses to queries. If the DNS is busy and sending many
	queries to WINS, and the WINS server is busy, it is possible for the XID value
	to be reused by the DNS server before the WINS server returns the result for the
	first query using the same XID. The DNS server looks for the first matching XID
	in the list it was tracking, and returns the IP address in that response to the
	DNS client.
	
	RESOLUTION
	==========
	
	The DNS now uses a larger number of unique XIDs. It also performs a check to be
	sure that the name returned by the WINS server matches the name queried on
	before returning the IP address to the requesting client.
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next Windows NT
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time                  Size    File Name     Platform
	  --------------------------------------------------------------
	  11/17/98  02:23p               176,912  Dns.exe       (x86)
	  11/17/98  02:23p               297,232  Dns.exe       (Alpha)
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	Additional query words: 4.00
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
