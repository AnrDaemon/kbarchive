---
layout: page
title: "Q182821: XFOR: Internet Mail Service Not Trying Next Exchange Record"
permalink: /kb/182/Q182821/
---

## Q182821: XFOR: Internet Mail Service Not Trying Next Exchange Record

{% raw %}

	Article: Q182821
	Product(s): Microsoft Exchange
	Version(s): 5.0 5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 05-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server Internet Mail Service does not fail over to the
	next Exchange record for a given domain, and the message is eventually returned
	to the sender with a non-delivery report (NDR).
	
	CAUSE
	=====
	
	The Internet Mail Service failed to try the next Exchange record if the host for
	the first Exchange record accepted the TCP three-way handshake (Syn-SynAck-Ack).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server version 5.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	This fix has been posted to the following Internet location:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/fixes/Eng/Exchg5.0/Post-SP2-IMS/
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information about obtaining the
	Service Pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	By examining a network trace of a computer exhibiting this behavior, you will
	see the following conversation occur:
	
	1. The Internet Mail Service queries the Domain Name Service (DNS) server for
	  the domain in question.
	
	  For example, in the following packet, a query has been generated to find all
	  Exchange records for SampleOrg.com, as can be seen in the DNS: Question
	  Section below:
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x6F0A; Proto = UDP; Len: 57
	   + UDP: Src Port: Unknown, (1146); Dst Port: DNS (53); Length = 37 (0x25)
	    DNS: 0x5:Std Qry for SampleOrg.com. of type Mail Xchg on class INET addr.
	        DNS: Query Identifier = 5 (0x5)
	      + DNS: DNS Flags = Query, OpCode - Std Qry, RD Bits Set, RCode - No
	   error
	        DNS: Question Entry Count = 1 (0x1)
	        DNS: Answer Entry Count = 0 (0x0)
	        DNS: Name Server Count = 0 (0x0)
	        DNS: Additional Records Count = 0 (0x0)
	        DNS: Question Section: SampleOrg.com. of type Mail Xchg on class INET
	   addr.
	            DNS: Question Name: SampleOrg.com.
	            DNS: Question Type = Mail exchange
	            DNS: Question Class = Internet address class
	
	
	2. The DNS server returns the list of Exchange records it has for the domain in
	  question.
	
	  For example, in the packet, the DNS server responds as can be seen in the DNS:
	  Answer Section below. From this section of the packet, we know that the DNS
	  server knows of two Exchange records for SampleOrg.com: Server1 with a
	  preference of 100 and Server2 with a preference of 300.
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0xC482; Proto = UDP; Len: 527
	   + UDP: Src Port: DNS, (53); Dst Port: Unknown (1146); Length = 507 (0x1FB)
	    DNS: 0x5:Std Qry Resp. for SampleOrg.com. of type Mail Xchg on class INET
	    addr.
	        DNS: Query Identifier = 5 (0x5)
	      + DNS: DNS Flags = Response, OpCode - Std Qry, AA RD RA Bits Set, RCode
	    - No error
	        DNS: Question Entry Count = 1 (0x1)
	        DNS: Answer Entry Count = 2 (0x2)
	        DNS: Name Server Count = 5 (0x5)
	        DNS: Additional Records Count = 2 (0x2)
	        DNS: Question Section: SampleOrg.com. of type Mail Xchg on class INET
	    addr.
	            DNS: Question Name: SampleOrg.com.
	            DNS: Question Type = Mail exchange
	            DNS: Question Class = Internet address class
	        DNS: Answer section: SampleOrg.com. of type Mail Xchg on class INET
	    addr.(8 records present)
	            DNS: Resource Record: SampleOrg.com. of type Mail Xchg on class
	    INET addr.
	                DNS: Resource Name: SampleOrg.com.
	                DNS: Resource Type = Mail exchange
	                DNS: Resource Class = Internet address class
	                DNS: Time To Live = 7200 (0x1C20)
	                DNS: Resource Data Length = 10 (0xA)
	                DNS: Preference = 100 (0x64)
	                DNS: Exchange Mailbox: Server1.SampleOrg.com.
	            DNS: Resource Record: SampleOrg.com. of type Mail Xchg on class
	     INET addr.
	                DNS: Resource Name: SampleOrg.com.
	                DNS: Resource Type = Mail exchange
	                DNS: Resource Class = Internet address class
	                DNS: Time To Live = 7200 (0x1C20)
	                DNS: Resource Data Length = 11 (0xB)
	                DNS: Preference = 300 (0x12C)
	                DNS: Exchange Mailbox: Server2.SampleOrg.com.
	      + DNS: Authority Section: SampleOrg.com. of type Auth. NS on class INET
	     addr.(5 records present)
	      + DNS: Additional Records Section: Server1.SampleOrg.com. of type Host
	     Addr on class INET addr.(2 records present)
	
	3. The Internet Mail Service queries the DNS server for the Host information of
	  the Exchange record with the lowest preference value.
	
	  For example, in the following packet, a query has been generated to find the
	  Host Address for Server1.SampleOrg.com, as can be seen in the DNS: Question
	  Section below.
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x700A; Proto = UDP; Len: 64
	   + UDP: Src Port: Unknown, (1147); Dst Port: DNS (53); Length = 44 (0x2C)
	     DNS: 0x1:Std Qry for Server1.SampleOrg.com. of type Host Addr on class
	    INET addr.
	        DNS: Query Identifier = 1 (0x1)
	      + DNS: DNS Flags = Query, OpCode - Std Qry, RD Bits Set, RCode - No
	    error
	        DNS: Question Entry Count = 1 (0x1)
	        DNS: Answer Entry Count = 0 (0x0)
	        DNS: Name Server Count = 0 (0x0)
	        DNS: Additional Records Count = 0 (0x0)
	        DNS: Question Section: Server1.SampleOrg.com. of type Host Addr on
	    class INET addr.
	            DNS: Question Name: Server1.SampleOrg.com.
	            DNS: Question Type = Host Address
	            DNS: Question Class = Internet address class
	
	4. The DNS returns the IP address of the server in question.
	
	  For example, in the following packet, the DNS server responds as can be seen
	  in the DNS: Answer Section below. From this section of the packet, you see
	  that the IP address of Server1 is 200.200.200.1.
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0xC483; Proto = UDP; Len: 274
	   + UDP: Src Port: DNS, (53); Dst Port: Unknown (1147); Length = 254 (0xFE)
	     DNS: 0x1:Std Qry Resp. for Server1.SampleOrg.com. of type Host Addr on
	     class INET addr.
	        DNS: Query Identifier = 1 (0x1)
	      + DNS: DNS Flags = Response, OpCode - Std Qry, RD RA Bits Set, RCode -
	     No error
	        DNS: Question Entry Count = 1 (0x1)
	        DNS: Answer Entry Count = 1 (0x1)
	        DNS: Name Server Count = 5 (0x5)
	        DNS: Additional Records Count = 5 (0x5)
	        DNS: Question Section: Server1.SampleOrg.com. of type Host Addr on
	     class INET addr.
	            DNS: Question Name: Server1.SampleOrg.com.
	            DNS: Question Type = Host Address
	            DNS: Question Class = Internet address class
	        DNS: Answer section: Server1.SampleOrg.com. of type Host Addr on
	     class INET addr.
	            DNS: Resource Name: Server1.SampleOrg.com.
	            DNS: Resource Type = Host Address
	            DNS: Resource Class = Internet address class
	            DNS: Time To Live = 636 (0x27C)
	            DNS: Resource Data Length = 4 (0x4)
	            DNS: IP address = 200.200.200.1
	      + DNS: Authority Section: SampleOrg.com. of type Auth. NS on class INET
	     addr.(5 records present)
	      + DNS: Additional Records Section: ns.SampleOrg.com. of type Host Addr
	     on class INET addr.(5 records present)
	
	5. The Internet Mail Service now initiates a TCP connection to Server1.
	
	  This is done with the following three packets, which is known as the TCP
	  three-way handshake (Syn-SynAck-Ack).
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x730A; Proto = TCP; Len: 44
	   + TCP: ....S., len:    4, seq:   3447617-3447620, ack:         0, win:
	   8192, src: 1145  dst:   25 (SMTP)
	  
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x292B; Proto = TCP; Len: 44
	   + TCP: .A..S., len:    4, seq:2120192000-2120192003, ack:   3447618, win:
	   4096, src:   25 (SMTP)  dst: 1145
	  
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x740A; Proto = TCP; Len: 40
	   + TCP: .A...., len:    0, seq:   3447618-3447618, ack:2120192001, win:
	   8760, src: 1145  dst:   25 (SMTP)
	
	6. IMPORTANT NOTE: The following packet is never received in the failing case.
	  In a normal working situation (that is, there is an SMTP daemon listening on
	  Server1), the next packet contains the SMTP Service Ready banner. If Server1
	  does not send an SMTP Service Ready banner, the Internet Mail Service
	  continues to try this same Exchange record until the message times out and an
	  NDR is sent to the sender.
	
	   + FRAME: Base frame properties
	   + ETHERNET: ETYPE = 0x0800 : Protocol = IP:  DOD Internet Protocol
	   + IP: ID = 0x9485; Proto = TCP; Len: 118
	   + TCP: .AP..., len:   78, seq:2034176001-2034176078, ack:   3332995, win:
	   4096, src:   25 (SMTP)  dst: 1145
	    SMTP: Rsp: Service ready, 78 bytes
	        SMTP: Response = 220 Server1.SampleOrg.com Microsoft Exchange
	   Internet Mail Service 5.0.1458.49 ready
	
	Additional query words: IMC
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : 5.0 5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
