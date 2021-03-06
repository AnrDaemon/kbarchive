---
layout: page
title: "Q138053: XFOR: How to Stop Winmail.dat from Being Sent to Internet Users"
permalink: /kb/138/Q138053/
---

## Q138053: XFOR: How to Stop Winmail.dat from Being Sent to Internet Users

{% raw %}

	Article: Q138053
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbusage exc4
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, version 4.0 
	- Microsoft Exchange Windows 95/98 client, version 4.0 
	- Microsoft Exchange Windows NT client, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how either an Exchange Server administrator or end users
	can prevent the Winmail.dat attachment from being sent to Internet users when
	using the Microsoft Exchange Internet Mail Connector (IMC).
	
	When an end user sends mail to the Internet from an Exchange Windows or Outlook
	client, a file attachment called Winmail.dat may be automatically added to the
	end of the message if the recipient's client cannot receive messages in Rich
	Text Format (RTF). The Winmail.dat file contains Exchange Server RTF information
	for the message, and may appear to the recipient as a binary file. It is not
	useful to non-Exchange Server recipients.
	
	MORE INFORMATION
	================
	
	To control whether or not to send messages in RTF, follow the option that best
	meets your situation:
	
	- Creating Custom Recipients
	  When an administrator creates a custom recipient using the Microsoft Exchange
	  Administrator program, click to clear the "Always Send To This Recipient In
	  Microsoft Exchange Rich-Text Format" check box.
	
	- Modifying Existing Microsoft Exchange and Custom Recipients
	  An administrator can prevent an existing user account (Microsoft Exchange user
	  or custom recipient) from sending RTF information by clicking to clear the
	  MAPI Recipient check box on the Advanced property page of the recipient's
	  properties. An administrator can view the recipient's properties by clicking
	  the recipient name, and then clicking Properties on the File menu.
	
	- Addresses in the Personal Address Book
	  End users can modify the Internet addresses in a personal address book (PAB)
	  to prevent sending RTF information by clicking to clear the "Always Send To
	  This Recipient In Microsoft Exchange Rich-Text Format" check box in the SMTP
	  - Address property page of the Internet address in the PAB. To obtain the
	  properties of an entry in the PAB, click the entry, and then on the File
	  menu, click Properties.
	
	- Configuring the Internet Mail Connector (IMC)
	  An administrator can configure the IMC with RTF options in the following
	  manner:
	
	  1. Open the Internet Mail Connector Properties page.
	
	  2. Click the General tab.
	
	     The "Send Microsoft Exchange Rich Text" list box controls the sending of
	     rich-text data. There are three values to choose from:
	
	      - If the value is set to User, the recipient properties are used to
	        determine whether or not to send RTF information.
	
	      - If the value is set to Always, RTF information is always sent,
	        regardless of the recipient properties.
	
	      - If the value is set to Never, RTF information is never sent.
	
	An administrator can also configure the option to send RTF information on a
	domain-by-domain basis. To define e-mail domains and the message settings for
	that domain, click the E-Mail Domain button of the Internet Mail tab.
	
	- One-Off Addressing
	  Anyone can send e-mail to an Internet user from an Exchange or Outlook client
	  by using one-off addressing. One-off addressing allows you to send a message
	  to addresses that are not in the PAB, the global address list, or in any
	  recipient containers.
	
	  Depending on the type of the one-off address used, RTF information is or is
	  not sent with the message:
	
	   - Rich-Text Information Is Sent:
	
	     If the one-off address has the following format, RTF information is sent
	     with the message:
	
	  [SMTP:<SMTP Address>]
	
	     where <SMTP Address> is any valid SMTP address, for example:
	
	  user@microsoft.com
	
	     To verify that RTF information is sent:
	
	     1. In a new message, type the address in the SMTP address format in the To
	        field. On the Tools menu, click Check Names. You will see the SMTP
	        address without the "SMTP:" and the name is underlined.
	
	     2. Double-click the address to bring up its properties.
	
	        If the Always send to this recipient in Microsoft Exchange rich-text
	        format check box is selected, rich-text information (the Winmail.dat
	        file) is sent along with the message.
	
	   - Rich-Text Information Is Not Sent:
	
	     If an end user is using a one-off address and does not want to send RTF
	     information to the recipient, the address should have the following
	     format:
	
	  <SMTP Address>
	
	     where <SMTP Address> is any valid SMTP address, for example:
	
	  user@microsoft.com
	
	NOTE: Unlike the address in the "Rich-Text Information Is Sent" section, the SMTP
	address is not proceeded by "SMTP:" and the address is not enclosed in square
	brackets ([]).
	
	If the Check Names check box is selected, the properties of the address will show
	that the rich-text option is not selected.
	
	However, no matter what option is selected for the address of the recipient, the
	IMC settings determine whether or not RTF information is transmitted. If the IMC
	is set to never send RTF information, even if the properties of the recipient
	address have the rich-text option selected, no RTF information is transmitted.
	
	If the IMC has separate settings for individual domains, the settings for those
	domains takes precedence for all messages addressed to users in those domains.
	
	Optionally, instead of typing the hex value in the edit field, click Editor,
	select File Version, and then click OK. On the File Version tab, in the fields
	provided, type the appropriate build number of Imcadmin.dll in the following
	format 5.5.2650.24. To determine the correct build number of Imcadmin.dll, do a
	search for the file on the Exchange Server. Once you have found it, right-click
	it, click Properties, and then click the Version tab. The build number
	appropriate to your server is listed here. Type this number into the value field
	and click OK. You then see the appropriate Hex value in the edit field.
	
	Additional query words: rtf internet mail .dat
	
	======================================================================
	Keywords          : kbusage exc4 
	Technology        : kbExchangeSearch kbExchange400 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange400NT kbExchange400Win95
	Version           : WINDOWS:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
