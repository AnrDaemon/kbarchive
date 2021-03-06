---
layout: page
title: "Q313660: SMS: DDM Assigns Clients Incorrectly in Multi-Tiered Hierarchy"
permalink: /kb/313/Q313660/
---

## Q313660: SMS: DDM Assigns Clients Incorrectly in Multi-Tiered Hierarchy

{% raw %}

	Article: Q313660
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbenv kbnetwork kbtool kbsms200 kbsms200bug kbDiscovery
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	In some situations, the Data Discovery Manager (DDM) component at a primary site
	will incorrectly process a client's Data Discovery Record (DDR) so that the
	client is assigned to a site to which it does not belong. This can occur when
	the client is installed in one TCP/IP subnet and it is later moved to another
	subnet. It is also possible to see this behavior by removing a TCP/IP subnet
	from one site's boundaries, and then adding it to another site's boundaries.
	
	In this situation a primary site combines both the new and old subnet data in the
	DDR which is forwarded to another site. Subsequently, this can cause client
	assignment and installation problems.
	
	CAUSE
	=====
	
	This problem occurs when a primary site forwards discovery data to another site
	(its parent or a secondary child site). The DDM component appends the new subnet
	data to the existing subnet data it has in the database. If the new subnet and
	old subnet data are not the same, the parent site interprets that the client
	resides in both subnets.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server (SMS) service
	pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The post-SMS 2.0 Service Pack 3 (SP3) version of this fix should have the
	following file attributes or later:
	
	  Date       Time   File name   Platform
	  ---------------------------------------------
	  10-Jan-01  12:13  Update.sql  Intel and Alpha
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	The hotfix stops the propagation of old subnet data from one site to another, but
	it does not immediately correct the existing discovery data in the SMS database.
	
	WORKAROUND
	==========
	
	To work around this problem for any computer that shows old discovered TCP/IP
	subnets, delete that system's discovery data record from the All Systems
	collection. It is important to do this at the child primary site(s) and the
	central site to ensure that the old subnet data is completely removed.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	A common example of this problem occurs during the staging of secondary sites.
	Consider a three-tier hierarchy where the secondary sites are being installed in
	the same location as the central site and are later shipped to their production
	location. The secondary site servers are domain controllers and playing SMS
	Logon Point roles. The following steps describe how this problem develops. The
	central site is the first tier, the child primary is the second tier, and
	secondary sites are the third tier.
	
	1. A secondary site is installed in a subnet (10.10.10.0) which is within the
	  central site's boundaries. Its parent is the child primary site (second
	  tier).
	
	2. The SMS client is automatically installed on the secondary site. The client
	  is assigned to both the secondary site and the central site because they both
	  have the 10.10.10.0 subnet as a site boundary.
	
	3. The client's discovery information, which includes the subnet, is forwarded
	  to the child primary site (the second tier) and is stored in its database.
	
	4. After the secondary site is shipped to its production location (subnet
	  10.10.99.0), the client determines that it is no longer in the central site's
	  boundaries, and uninstalls itself from the central site.
	
	5. The new discovery data that contains the 10.10.99.0 subnet is forwarded to
	  the child primary site.
	
	6. During the processing of the discovery data, the child primary site appends
	  the old subnet data (10.10.10.0) to the new subnet data (10.10.99.0), and
	  then forwards this to the central site.
	
	7. During the processing of the client's discovery data, the central site sees
	  the old subnet, 10.10.10.0, which it still manages. It also sees the client
	  is not installed to the central site, and because of this, creates a Client
	  Configuration Request (CCR) to cause the CCM component to reinstall the
	  client to the central site.
	
	8. After the client is installed to the central site, it again determines that
	  it is not in the central site's boundaries, and uninstalls the client from
	  the central site.
	
	Unless the client's discovery data is deleted from the child primary site's
	database, this cycle can continue without end. If enough secondary sites are
	configured in this way, this behavior can have a significant impact on the
	available network bandwidth in a WAN environment.
	
	Another scenario could arise if SMS Remote Client Installation is enabled on the
	central site, and a client moves from a subnet that is managed by the central
	site to one that is managed by a secondary site. In the situation, the same
	client installation behavior could occur.
	
	Note that certain types of discovery do not replace the existing subnet data for
	a client, but only append to the existing subnet data. Specifically, network
	discovery and server discovery only append to the existing subnet data in the
	database. If the SMS client is installed on a discovered computer, the resulting
	heartbeat discovery or logon discovery data will replace the existing subnet
	data in the database. This occurs because the method that is used by network
	discovery and server discovery to obtain the subnet data is not considered as
	accurate as the method that is used by heartbeat and logon discovery.
	
	Because the subnet data is replaced by the client forms of discovery, it is
	possible for the child primary sites to show the correct data in its database.
	However, it still forwards the combined subnet data to the central site at least
	one time. Because the subnet data that is forwarded from a child primary site
	does not have the "replace flag" set, the central site then always shows the
	combined subnets that a client has resided in.
	
	A Related Problem
	-----------------
	
	Server discovery examines a remote computer's registry to determine the TCP/IP
	subnet for which the network adapter is configured. It is possible for a network
	adapter's protocol bindings to be disabled, and server discovery still reports
	its TCP/IP settings. In this situation, server discovery can persistently
	propagate invalid discovery data, and this may cause the behavior that is
	similar to the behavior that is described earlier in this article.
	
	Changing the registry values that are associated with the disabled TCP/IP
	protocol stops server discovery from reporting this information.
	
	NOTE: If you are using Microsoft Windows 2000 or later, it is preferable to just
	disable the entire network adapter. Otherwise, you must take care not to change
	the TCP/IP information for the network adapters that are currently in use.
	
	Server discovery enumerates the network adapters at the following registry
	location of a remote computer:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkCards
	
	Under each numbered key (1, 2, and so on) the value for ServiceName is retained.
	
	The actual TCP/IP information is then retrieved from the following registry
	location:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceName\Parameters\Tcpip
	
	For the network adapter that contains the old TCP/IP information, change the
	value of the TCP/IP address to 0.0.0.0. This effectively stops server discovery
	from reporting the TCP/IP address information for this network adapter.
	
	Installing the Hotfix
	---------------------
	
	To install the hotfix, use one of the following methods on all of the SMS primary
	site servers in the SMS hierarchy.
	
	Use the Hotfix Installer:
	
	NOTE: This method is only for use with Intel-based computers.
	
	1. Copy the hotfix folder structure to a share on your network. Q313660.exe is a
	  Microsoft SMS Installer file that updates specific files on your site server.
	
	2. Log on to your site server by using an account with administrative
	  privileges.
	
	3. On the site server, quit the SMS Administrator console.
	
	4. Run the Q313660.exe file, and then follow the directions in the wizard.
	
	Manual Installation:
	
	1. Stop the SMS Executive and the SMS Site Component Manager services on the
	  site server.
	
	2. Stop the SMS SQL Monitor service on the computer on which the SMS database is
	  located.
	
	3. Run the SQL Query Analyzer tool, and then connect to the SQL server on which
	  the SMS database is located with "sa" privileges.
	
	4. Click the SMS database in the list of databases.
	
	5. Open the Update.sql file that is located in the I386 or Alpha subfolder in
	  the hotfix folder structure.
	
	6. Run the query.
	
	7. Restart the SMS SQL Monitor, SMS Executive, and SMS Site Component Manager
	  services.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kbnetwork kbtool kbsms200 kbsms200bug kbDiscovery 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
