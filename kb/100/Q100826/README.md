---
layout: page
title: "Q100826: PC Ext: How External Sends Mail Between Postoffices"
permalink: /kb/100/Q100826/
---

## Q100826: PC Ext: How External Sends Mail Between Postoffices

{% raw %}

	Article: Q100826
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how the External Mail program (EXTERNAL.EXE) for version
	3.2 of Microsoft Mail for PC Networks delivers mail between postoffices. This
	process involves several files in the Mail database.
	
	MORE INFORMATION
	================
	
	The example shown below shows a typical file transfer of a single piece of mail
	from postoffice P: COMPANY/CORPORATE to Q: COMPANY/MAIL. First, External checks
	the postoffices for updates to user/group lists. These lists include all the new
	user lists and definitions that are defined in the postoffices through the Mail
	Administrator program (ADMIN.EXE).
	
	Example
	-------
	
	A user has composed a message on postoffice COMPANY/CORPORATE and has addressed
	the message to a user on COMPANY/MAIL. The message is written into the database
	for COMPANY/CORPORATE in the KEY, MBG, and MAI subdirectories. If an attachment
	is included, a file will be written to an ATT subdirectory.
	
	External then checks for any outgoing mail by opening and closing every external
	postoffice's KEY file. Flags within the files indicate if any mail is required
	to be sent.
	
	In this example, one mail item is going to be sent from CORPORATE to MAIL. First,
	External reads the .KEY, .MBG, and .MAI files on P: COMPANY/CORPORATE. The
	filename in the example is 00000116.MAI.
	
	The delivery by the External program is a two-part process called Dispatch and
	Mailer. The Dispatch program delivers the mail between the postoffices and the
	Mailer program processes the mail and places messages into recipients'
	mailbags.
	
	Dispatch
	--------
	
	NOTE: SESSION.LOG entries have been indented for reference.
	
	The External program first reads the P2 file (00000116.MAI) from the CORPORATE
	postoffice and writes it to the MAIL postoffice (N:MAI\MA8\00000278.MAI).
	
	  06-01-93 09:58 Transferring mail: mail file is: M:MAI\MA6\00000116.MAI.
	  06-01-93 09:58 Sending P2...
	  06-01-93 09:58 Target file: N:MAI\MA8\00000278.MAI
	
	The Dispatch program then writes to the P1 subdirectory the envelope of the mail
	message. The envelope contains a list of all the people to whom the mail message
	must be delivered. This includes the To field and the Cc field.
	
	  06-01-93 09:59 Sending P1...
	  06-01-93 09:59 Target file: N:P1\00000278.P1
	
	The External program then writes to the INQUEUE3.KEY and INQUEUE3.MBG files the
	name of the file in the P1 subdirectory that contains the recipients of the
	mail.
	
	This concludes the delivery of the mail.
	
	  06-01-93 09:59 P1 file successfully sent.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	
	Mailer
	------
	
	The Mailer program reads the INQUEUE3 files in the KEY and MBG subdirectory. The
	MBG queue contains the reference pointer (P1 subdirectory filename). The Mailer
	program then reads the references contained in the file in the P1 subdirectory
	and writes to each recipient's KEY file and MBG file a pointer to the mail item
	contained in the MAI subdirectory.
	
	  06-01-93 09:59 Processing received mail queue at: N: NETWORK/MAIL.
	  06-01-93 09:59 INQUEUE file: N:MAI\MA8\00000278.MAI
	  06-01-93 09:59 Delivering of mail from INQUEUE3 is complete.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	
	NOTE: A mail item that is sent to numerous people will contain a reference
	pointer for each person who is to receive the mail item; however, there will
	only be ONE .MAI file.
	
	  06-01-93 09:58 Sending mail (1)
	  06-01-93 09:58 From: NETWORK/CORPORATE
	  06-01-93 09:58 To: NETWORK/MAIL
	  06-01-93 09:58 Transferring mail: mail file is: M:MAI\MA6\00000116.MAI.
	  06-01-93 09:58 Sending P2...
	  06-01-93 09:58 Target file: N:MAI\MA8\00000278.MAI
	  06-01-93 09:59 Sending P1...
	  06-01-93 09:59 Target file: N:P1\00000278.P1
	  06-01-93 09:59 P1 file successfully sent.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	  06-01-93 09:59 Processing received mail queue at: N: NETWORK/MAIL.
	  06-01-93 09:59 INQUEUE file: N:MAI\MA8\00000278.MAI
	  06-01-93 09:59 Delivering of mail from INQUEUE3 is complete.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	  06-01-93 09:59 N: NETWORK/MAIL: Checking for dispatch mail...
	  06-01-93 09:59 No mail.
	  06-01-93 09:59 Delivering new mail to NETWORK/CORPORATE.
	  06-01-93 09:59 Delivering new mail to NETWORK/CORPORATE.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	  06-01-93 09:59 Delivering new mail to NETWORK/MAIL.
	
	Glossary
	--------
	
	  Term        Description
	  ----        -----------
	
	  ATT         Attachments subdirectory and attachments files.
	              Referenced by a pointer within the message contents
	              (.MAI file).
	
	  Contents    Contents of the message include the items such as the
	              date, time, subject, priority, attachments, and the
	              message itself. Another name for the .MAI file. In
	              visual terms, this equates to selecting a message from
	              the Inbox and reading its contents.
	
	  Envelope:   See P1.
	
	  MAI         See CONTENTS.
	
	  MBG, KEY    Combined, these two files are used to provide a list of
	              Inbox items that point to the mail message. This
	              equates to looking at the Inbox in the Mail program.
	
	  P2          Another name for the .MAI file; also known as the
	              contents of the message. This equates to the actual
	              message that was composed.
	
	  P1          An acronym for the addressing or the envelope of the
	              message. The envelope contains all the To and Cc
	              addresses the mail items are supposed to go to.
	
	
	Additional query words: 3.20 MTA
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
