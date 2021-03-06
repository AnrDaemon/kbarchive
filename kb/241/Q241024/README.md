---
layout: page
title: "Q241024: Slow File Access from Macintosh Client on Windows NT Server"
permalink: /kb/241/Q241024/
---

## Q241024: Slow File Access from Macintosh Client on Windows NT Server

{% raw %}

	Article: Q241024
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 13-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Macintosh clients may experience slow performance when they attempt to gain
	access to files on a Windows NT server running Services for Macintosh (SFM) if
	other clients are using AppleScripts to query for files on the server.
	
	CAUSE
	=====
	
	A program that uses AppleScript to use the Apple File Protocol (AFP) CatSearch
	command (such as Macintosh File Find) may reduce the server's responsiveness to
	other Macintosh clients on the network, causing them to appear to stop
	responding (hang) for brief periods of time. This problem occurs only when there
	is a large number of Macintosh clients connected to a Macintosh volume that
	contains a very large number of files and folders.
	
	If the AppleScript program is written to use a CatSearch command, it ignores the
	"DisableCatSearch=1" setting, which indicates that no CatSearch commands are
	allowed. Setting the "DisableCatSearch=1" setting in the registry disables
	Macintosh clients from using CatSearch commands, but not custom programs that
	use AppleScripts.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date      Time                 Size    File name     Platform
	  -------------------------------------------------------------
	  09/28/99  11:49a              134,416  Sfmsrv.sys    x86
	  09/28/99  11:48a              241,744  Sfmsrv.sys    Alpha
	
	
	
	To Disable CatSearch Commands for All Clients on an SFM Volume
	--------------------------------------------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	NOTE: This change is only valid on systems running Windows NT 4.0 Service Pack 2
	or later.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the volume on which you want to disable CatSearch commands under the
	  following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MacFile\Parameters\Volumes
	
	3. On the Edit menu, click Multi String, type "DisableCatSearch=1" (without the
	  quotation marks), and then click OK.
	
	4. Quit Registry Editor.
	
	5. Stop and then restart SFM.
	
	NOTE: In Windows 2000 the administrator applies only the Registry setting to
	enable this option. In Windows NT 4.0 the adminstrator must apply the binaries
	and the registry entry.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	This new functionality gives administrators the ability to turn off the
	CatSearch command. If this feature is disabled, AppleScript-based programs may
	not work. For additional information, click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q158796 Macintosh Clients Connected to Windows NT Server Appear to Hang
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search
	Version           : :2000,4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
