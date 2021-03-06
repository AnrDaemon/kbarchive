---
layout: page
title: "Q265215: DocErr: SMCLIENT.DOC Incorrectly References SpyHydra Application"
permalink: /kb/265/Q265215/
---

## Q265215: DocErr: SMCLIENT.DOC Incorrectly References SpyHydra Application

{% raw %}

	Article: Q265215
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft Windows 2000 Server Resource Kit ISBN 1-57231-805-8 
	- MSPRESS Microsoft Windows 2000 Professional Resource Kit ISBN 1-57231-808-2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article summarizes errors in SMCLIENT.DOC, which is included with the
	Windows 2000 Resource Kits.
	
	MORE INFORMATION
	================
	
	SMCLIENT.DOC Incorrectly References SpyHydra Application and Documentation
	--------------------------------------------------------------------------
	
	The SMCLIENT.DOC file that is included in the Windows 2000 Resource Kits listed
	above contains several references to the SpyHydra application and documentation.
	All references to SpyHydra should be changed to Spy++.
	
	The Spy++ application and corresponding documentation is not included with the
	Windows 2000 Resource Kits. Spy++ is a utility that is included with Visual C++
	and Visual Studio. The Spy++ tool produces output in hex, which can then be
	converted to signed decimal to be used in the SMClient scripts.
	
	In the Overview section of the SMCLIENT.DOC the second paragraph titled "How it
	works" should be changed to read:
	
	  "Terminal Server Client Simulation" application runs as a stand-alone
	  command-line application. The simulation would create a connection with
	  Terminal Server and issue appropriate commands to load/unload remote
	  sessions, run iostress, ntstress or the "Spy++" application to simulate
	  keyboard/mouse events. (For more information about the "Spy++" application,
	  see the "Spy++" documentation included with Visual C++ or Visual Studio.)
	
	Similarly, Section 2.2: The Scripting Language, outlines identifiers that are
	reserved for use as Client Simulation keywords. The following items that
	reference SpyHydra should be changed to reference the Spy++ application and
	documentation. These items include sections 2.2.4 Start, 2.2.5 Sendoutput, 2.2.6
	Senddata, 2.2.13 Job.
	
	In Section 3: Validation, the paragraph in example 1 should read:
	
	  "This job opens a connection with a Terminal Server, starts the "Spy++"
	  application in Spy mode and after that sends keyboard/mouse events to the
	  Terminal Server. Because "Spy++" is started in Spy mode, it verifies that all
	  inputs are received in the right order and none of these inputs are lost, and
	  also it creates a log file on the Terminal Server. This scenario can be used
	  to verify that the client-server connection works OK. Of course this is true
	  if and only if the Client Simulation will use the same code to connect with a
	  Terminal Server as the real Client."
	
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: 1-57231-808-2 1-57231-805-8 RKBOOK Reskit Resource Kit Win2000 Pro Terminal Server Capacity Planning Tools
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
