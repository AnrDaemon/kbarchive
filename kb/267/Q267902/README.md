---
layout: page
title: "Q267902: Applications Fail to Receive Data When Opening LUA LU"
permalink: /kb/267/Q267902/
---

## Q267902: Applications Fail to Receive Data When Opening LUA LU

{% raw %}

	Article: Q267902
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0 SP3
	Operating System(s): 
	Keyword(s): kbSNA400sp4fix kbSNA400PreSP4fix
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade to SNA Server 4.0 to Service Pack 3, an LUA RUI application
	cannot open a new LUA Pooled session. After running for several days, the
	application fails to receive any host data after opening a new session from an
	LUA pool. The SNA Server 3270 and DLC or SNA message traces show that the SNA
	Server service receives an OPEN SSCP request from the LUA application, but it
	never sends a new NOTIFY(SLU Enabled) message to the host. Therefore, the LUA
	application never receives any host data over the session.
	
	This problem may also occur in 3270 sessions with any 3270 emulator.
	
	CAUSE
	=====
	
	This problem is inadvertently introduced when the fix described in the following
	Knowledge Base article is implemented:
	
	  Q235959 SNA Server May Fail to Reestablish a Session Under Certain Conditions
	
	Due to this update, SNA Server incorrectly discards the host TERMSELF response
	when the SNA sequence number on the session is set to X'7FFF'. Further attempts
	to open the session succeed, but the SNA Server fails to send any further
	messages on the SSCP-LU session.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version 4.0
	Service Pack 3.
	
	This problem was first corrected in SNA Server 4.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	This problem causes SNA Server to discard any host response on an SSCP-LU
	session that has a SNA sequence number of 0x7FFF. This will likely cause the LU
	to stop responding (hang). The following excerpt from an SNA Server 3270 and DLC
	message trace exhibits this problem, showing the last messages that flow over LU
	#02. The node never sends the NOTIFY(SLU Disabled) after it receives the UNBIND
	+RSP. Note that the SNA sequence number for the TRMSLF (TERMSELF) response
	received on the SSCP-LU session is 0x7FFF.
	
	NOTE: SNA traces may vary from the following example.
	
	  
	
	  |0000009a.0000009c FMI   ----------------------------------------------- 09:46:13.0226
	  |0000009a.0000009c FMI   0B1D0001->01020202 CLOSE SSCP REQUEST
	  |0000009a.0000009c FMI
	  |0000009a.0000009c FMI   ---- Header  at address 01194C6C, 0 elements ----
	  |0000009a.0000009c FMI   01011101 E0000000 00000002 01000C01     
	  |0000009a.0000009c FMI   ----------------------------------------------- 09:46:13.0226
	  |0000009a.0000009c FMI   01020202->0B1D0001 CLOSE SSCP RSP OK
	  |0000009a.0000009c FMI
	  |0000009a.0000009c FMI   ---- Header  at address 01194C6C, 0 elements ----
	  |0000009a.0000009c FMI   02011101 E0000000 00000002 01000C01     
	  |0000009a.0000009c DLC   ----------------------------------------------- 09:46:13.0236
	  |0000009a.0000009c DLC   01020101->04161000 DLC DATA
	  |0000009a.0000009c DLC                      DAF:00 OAF:02 ODAI:off Normal
	  |0000009a.0000009c DLC                      TRMSLF RQD FMD FI BC EC DR1
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Header  at address 0119548C, 1 elements ----
	  |0000009a.0000009c DLC   03B0B006 00002C00 00027FFF 01000C01     
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Element at address 01B89698, start 10, end 18 ----
	  |0000009a.0000009c DLC   0B800001 068300F3 00                    
	  |0000009a.0000009c DLC   ----------------------------------------------- 09:46:14.0217
	  |0000009a.0000009c DLC   04161000->01020101 DLC DATA
	  |0000009a.0000009c DLC                      DAF:02 OAF:00 ODAI:off Normal
	  |0000009a.0000009c DLC                      TRMSLF +RSP FMD FI BC EC DR1
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Header  at address 01194B68, 1 elements ----
	  |0000009a.0000009c DLC   06050100 00002C00 02007FFF 01000C01     
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Element at address 01B8932C, start 10, end 15 ----
	  |0000009a.0000009c DLC   8B800001 0683                           
	  |0000009a.0000009c DLC   ----------------------------------------------- 09:46:15.0169
	  |0000009a.0000009c DLC   04161000->01020101 DLC DATA
	  |0000009a.0000009c DLC                      DAF:02 OAF:01 ODAI:off Exp.
	  |0000009a.0000009c DLC                      UNBIND RQD SC  FI BC EC DR1
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Header  at address 01194E40, 1 elements ----
	  |0000009a.0000009c DLC   06060100 00002D00 020145D0 01000C01     
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Element at address 01B860FC, start 10, end 14 ----
	  |0000009a.0000009c DLC   6B800032 01                             
	  |0000009a.0000009c DLC   ----------------------------------------------- 09:46:15.0169
	  |0000009a.0000009c DLC   01020101->04161000 DLC DATA
	  |0000009a.0000009c DLC                      DAF:01 OAF:02 ODAI:off Exp.
	  |0000009a.0000009c DLC                      UNBIND +RSP SC  FI BC EC DR1
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Header  at address 01194E40, 1 elements ----
	  |0000009a.0000009c DLC   06060100 00002D00 010245D0 01000C01     
	  |0000009a.0000009c DLC
	  |0000009a.0000009c DLC   ---- Element at address 01B860FC, start 10, end 13 ----
	  |0000009a.0000009c DLC   EB800032
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSNA400sp4fix kbSNA400PreSP4fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400SP3
	Version           : WINDOWS:4.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
