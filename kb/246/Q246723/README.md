---
layout: page
title: "Q246723: How to Programmatically Timeout an (MC_)ALLOCATE Verb"
permalink: /kb/246/Q246723/
---

## Q246723: How to Programmatically Timeout an (MC_)ALLOCATE Verb

{% raw %}

	Article: Q246723
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Operating System(s): 
	Keyword(s): kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how a developer can use the APPC WinAsyncAPPCEx()
	function in combination with the Win32 WaitForSingleObjectEx() to expire an
	(MC_)ALLOCATE verb when a predefined time-out interval has elapsed.
	
	Microsoft does not recommend canceling an outstanding [MC_]ALLOCATE unless the
	request has been outstanding for a reasonable period of time (at least 20
	seconds). If [MC_]ALLOCATE is issued with rtn_ctl = AP_WHEN_SESSION_ALLOCATED,
	the request does not complete until an available bound LU6.2 session is
	allocated from an SNA Server computer that supports the Local LU/ Remote LU/Mode
	being requested. A couple possible causes for slow [MC_]ALLOCATE response time
	include the following:
	
	- If all available LU6.2 sessions are already in use, then the [MC_]ALLOCATE
	  will block until a current conversation ends, creating an available LU6.2
	  session. If this is occurring frequently, consider increasing the parallel
	  session limit in the SNA Server Mode and the remote application subsystem.
	
	- If the APPC LU session is supported through an on-demand connection, and the
	  connection is slow to activate (such as over SDLC)
	
	Also, in order for the SNA Server computer(s) to properly handle cancelled
	[MC_]ALLOCATE requests, the computer(s) should be running at least SNA Server
	4.0 SP2 or greater. For additional information, click the article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q195996 SNA Server Incorrectly Handles Cancelled Allocate Requests
	
	MORE INFORMATION
	================
	
	When you use the following sample code, an APPC Allocate request will timeout if
	it has not completed in 25 seconds. This code is used for demonstration purposes
	only.
	
	The following code snippet begins with construction of the verb control block
	(vcb) used for the Allocate request. When the vcb is complete, a pointer to the
	vcb is passed to the WinAsyncAPPCEx() function along with a Win32 handle used
	for event notification. The handle that is passed to the WinAsyncAPPEx()
	function is also registered with the WaitForSingleObjectEx(). The second
	argument specified in the WaitFOrSingleObjectEx is the timeout value specified
	in milliseconds. If the function succeeds, the return value indicates the event
	that caused the function to return. If the return value is WAIT_TIMEOUT, then
	the function completed as a result of the expired timer.
	
	For more details concerning APPC Programming and Win32 APIs, please see the
	Microsoft Platform SDK.
	
	   ...
	   ...
	
	    // Construct verb control block (vcb)
	
	    vcb->allocate.opcode = AP_B_ALLOCATE;
	    vcb->allocate.opext = AP_BASIC_CONVERSATION;
	    vcb->allocate.conv_type = AP_BASIC_CONVERSATION;
	    memcpy( vcb->allocate.tp_id,TPid, 8);
	    vcb->allocate.sync_level = AP_CONFIRM_SYNC_LEVEL;
	    vcb->allocate.rtn_ctl = AP_WHEN_SESSION_ALLOCATED;
	    FillMemory(vcb->allocate.plu_alias,sizeof(vcb->allocate.plu_alias),0x20);
	    CopyMemory(vcb->allocate.plu_alias,RLUName,strlen(RLUName) );<BR/>
	    FillMemory(vcb->allocate.mode_name,sizeof(vcb->allocate.mode_name),0x20);
	    CopyMemory(vcb->allocate.mode_name,ModeName, strlen(ModeName) );
	    ConvertAToE(vcb->allocate.mode_name, 8);
	    FillMemory(vcb->allocate.tp_name, sizeof(vcb->allocate.tp_name), 0x20);
	    CopyMemory(vcb->allocate.tp_name, "GREGORY", 7);
	    ConvertAToE(vcb->allocate.tp_name,64);
	    vcb->allocate.security = AP_NONE;
	
	    
	    // Create an unnamed event object
	    hHandle = CreateEvent(NULL, FALSE, FALSE, NULL);
	
	    // - Use async entry point for the verb.
	    // - Pass the event handle (created above) along with pointer to vcb
	
	    verbid = WinAsyncAPPCEx(hHandle,(long)vcb);
	
	  if (verbid == 0)
	  	{
	  		
	  		return false;
	  	}
	
	  	// Sleep for 25 seconds before timing out 
	
	  	wait_code = WaitForSingleObjectEx(hHandle,25000,true);
	  	ASSERT(wait_code != WAIT_ABANDONED); 
	  	if (wait_code == WAIT_TIMEOUT)
	  	{
	  		//failed 
	
	                  WinAPPCCancelAsyncRequest(verbid);
	  		CloseHandle(hHandle);
	  		return false;
	  	}
	  	CloseHandle(hHandle);
	  	// Allocate successful. Return and do more useful things
	  	return true;
	  }
	   ...
	   ...
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
