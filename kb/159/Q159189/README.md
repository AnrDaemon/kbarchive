---
layout: page
title: "Q159189: XFOR: DXA Drops Transaction if X400 DDA Value Contains a Slash"
permalink: /kb/159/Q159189/
---

## Q159189: XFOR: DXA Drops Transaction if X400 DDA Value Contains a Slash

{% raw %}

	Article: Q159189
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform Directory Synchronization between Microsoft Exchange Server and
	Microsoft Mail for PC Networks, the following error(s) may appear in the event
	viewer application log:
	
	  Event ID: 13
	  Source: X400Proxy
	  Type: Warning
	  Category: None
	  Description: X400 address failure. An illegal type name was specified at
	  character position 41 of 'X400:O=ABB;ou1=CHNET;G=URS ;
	  F/S=MUELLER;p=ABB;a=400NET;c=CH;'.
	
	  Event ID: 247
	  Source: MSExchangeDX
	  Type: Error
	  Category: MS Mail 3.2
	  Description: The e-mail address of the following transaction is not a valid
	  format. See previous events logged by the Microsoft Exchange System Attendant
	  component for details. The transaction is A MUELLER URS / F (CHNET)
	  X400:/C=CH/A=400NET/P=ABB/O=ABB/OU=CHNET/G=URS / F/S=MUELLER. (Thread 0) The
	  custom recipient (CR) has not been created on the Exchange Server.
	
	CAUSE
	=====
	
	The Microsoft Exchange Directory Synchronization Agent (DXA) does not properly
	handle incoming X.400 addresses that contained a forward slash (or solidus) as
	part of a DDA Value. When the DXA encounters a forward slash as part of a DDA
	value it reports an error and aborts the transaction. The X.400 custom recipient
	is not created in Microsoft Exchange Server .
	
	RESOLUTION
	==========
	
	Apply the fix referenced below. The updated Microsoft Exchange DXA will now
	allow the forward slash as part of an X.400 DDA value and create the custom
	recipient in the Microsoft Exchange Directory. A forward slash (or solidus) is a
	valid character in a DDA value as defined by the CCITT (see the More Information
	section below).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange version 4.0.
	This problem was corrected in the latest Microsoft Exchange 4.0 U.S. Service
	Pack. For information on obtaining the service pack, query on the following word
	in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	The 1988 CCITT Blue Book defines that a DDA value can contain a printable
	string. The 1988 Blue Book defines the list of printable strings as follows:
	
	  PrintableString char-set is as follows (per Blue Book X.208, Table 5):
	
	  Capital lettersA, .. Z
	  Small lettersa, .. z
	  Digits0, .. 9
	  Space
	  Apostrophe'
	  Left paren(
	  Right paren )
	  Plus sign+
	  Comma,
	  Hyphen-
	  Full stop.
	  Solidus/ 
	  Colon:
	  Equal sign=
	  Question mark?
	
	Additional query words: x400
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
