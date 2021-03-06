---
layout: page
title: "Q122180: Systems Management Server Event Log Codes 250 Through 349"
permalink: /kb/122/Q122180/
---

## Q122180: Systems Management Server Event Log Codes 250 Through 349

{% raw %}

	Article: Q122180
	Product(s): Microsoft Systems Management Server
	Version(s): 1.0,1.1
	Operating System(s): 
	Keyword(s): kbnetwork kbDatabase kbScheduler smsdatabase smsscheduler
	Last Modified: 05-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	This article details Systems Management Server event log codes 250 through
	349.
	
	Event Log Codes 250 - 349
	-------------------------
	
	Code   Description
	----   -----------
	
	250    Cannot create new thread. Verify there is enough virtual memory on
	      the machine.
	
	251    Cannot connect to site A over LAN. Verify the remote site server B
	      is on the LAN and share C is visible and has all the necessary
	      permission for the SMS service account. Also verify the network is
	      not saturated. Verify you can move large amount of data across the
	      network. Win32Error Code = D.
	
	252    Cannot connect to site A over RAS. Verify the remote site server B
	      is alive and running RAS Server Serivce, and the phone book entry C
	      in the default phone book contains valid information Win32 Error
	      Code = D. Check the RAS section in the NT document for detailed
	      explanation on the error code.
	
	253    Sender had a successful RAS connection to site A. However it failed
	      to connect to share B on server C using the given user name and
	      password. Verify the share permission is set up properly. Win32
	      Error Code = D
	
	254    Cannot start TP using local LU alias A while establishing a SNA
	      connection to site B. The primary return code is C, the secondary
	      return code is D. Verify all the SNA setting are correct through the
	      SNA Admin.
	
	255    Cannot do a MC_ALLOCATE while establishing a SNA connection to site
	      A. The primary return code is B, the secondary return code is C.
	      Verify all the SNA setting are correct through the SNA Admin.
	
	256    Cannot find an active receiver at remote site A to confirm the
	      connection request. Verify the SNA receiver is running at the remote
	      site.
	
	257    The X adddress string is invalid. It's missing the remote server
	      name section.
	
	258    The X adddress string is invalid. It's missing the remote share name
	      section.
	
	259    The X adddress string is invalid. It's missing the remote gateway
	      name section.
	
	260    A Sender is starting for send request
	
	261    Incorrect invocation of a sender.
	
	262    Cannot open status file X.
	
	263    Cannot read status file X.
	
	264    No remote addresses in status file X.
	
	265    Connection to remote site failed after retries exceeded. No more
	      remote addresses in status file X.
	
	266    Remote site installation failed with error X.
	
	267    No errors reported from remote site installation.
	
	268    Cannot locate the package file or it is of zero length. File name X.
	
	269    Cannot locate the instruction file or it is of zero length. File
	      name X.
	
	270    File X exists.
	
	271    File X exists. It has been renamed.
	
	272    Job X was successfully sent to destination Y.
	
	273    The dispatcher failed to spawn a sender process for send request X.
	      The system returned the above error code.
	
	274    No remote address present.
	
	275    The remote address is inavlid. Address: X.
	
	276    Local address missing or invalid.
	
	277    Failed to connect to destination X.
	
	278    Failed to disconnect from remote resource X.
	
	279    Failed to connect to RAS Server. Remote resource X. The error code
	      from RAS is reported above.
	
	280    Failed to open file X.
	
	281    Failed to open file X. LU aliases: Y.
	
	282    Failed to close file X.
	
	283    Failed to close file X. LU aliases: Y.
	
	284    File X is not the expected size.
	
	285    Write to file X failed. The sender failed to confirm that the file
	      was written to correctly.
	
	286    Failed to flush file X.
	
	287    Failed to flush file X. LU aliases: X.
	
	288    Failed to read file X.
	
	289    Insufficient disk space on X.
	
	290    Insufficient disk space on X. LU aliases: Y.
	
	291    Failed to check the disk space on remote machine X. Possible causes
	      are: The remote machine is unavailable. Incorrect access rights to
	      the remote machine.
	
	292    Failed to rename remote file from X to Y.
	
	293    Failed to remove file X.
	
	294    Failed to remove file X. LU aliases: Y.
	
	295    Memory allocation failed.
	
	296    Dispatcher starting.
	
	297    SNA Receiver starting.
	
	298    SNA Receiver stopping.
	
	299    RAS Dispatcher cannot get access to the RAS section of the registry.
	
	300    Dispatcher has terminated.
	
	301    Dispatcher has terminated due to an error.
	
	302    Sender has received a message to stop the current transfer.
	
	303    Sender has received a message to cancel the current transfer.
	
	304    Sender has received a message to suspend the current transfer.
	
	305    Failed to establish connection between local LU X and remote LU Y.
	
	306    The SNA communication with the remote site failed. Local LU alias X,
	      Remote LU alias Y.
	
	307    The application failed to set a notification event on the above
	      directory. The API has returned the error code above.
	
	308    The application failed to create a handle. The API has returned the
	      error code above.
	
	309    Incomplete data. Either the destination site or the instruction type
	      is missing.
	
	310    Cannot access the registry.
	
	311    Missing in-box path in registry.
	
	312    Failed to construct the instruction file.
	
	313    The package source directory cannot be found.
	
	314    Failed to update the job source.
	
	315    The job handler encountered an error attempting to place the send
	      request in the unscheduled outbox. Possible causes are: the server
	      holding the Scheduler's unscheduled outbox is not reachable (server
	      may be off the network); or there may already be a send request with
	      the same ID (A) in the unscheduled outbox (should not happen).
	
	316    The job encountered an error while sending data or performing
	      operations relating to the destination site. Possible causes are: X
	      addresses to the destination site may be invalid (server or account
	      information may be incorrect); the destination site server may not
	      be running; or there may be communications or other sending-related
	      errors.
	
	317    The job encountered an error while sending a remote cancel
	      instruction. The job information has already reached the destination
	      site, requiring a cancel instruction to be sent to that destination
	      site, informing the site to stop processing the job. Possible causes
	      are: addresses to the destination site may be invalid (server or
	      account information may be incorrect); the destination site server
	      may not be running; or there may be communications or other sending-
	      related errors.
	
	318    The job cannot access the specified query (A) and therefore cannot
	      generate the list of target workstations for the job. Possible
	      causes are: SQL server is not responding; a blank queryname was
	      specified; or the query was deleted after the job was created.
	
	319    The job encountered an error trying to process the specified machine
	      path (A) and therefore cannot generate the list of target
	      workstations for the job. Possible causes are: an invalid site name
	      or site code was specified (site groups are not allowed); the PC
	      architecture has not been defined yet; or a fatal low-memory
	      condition was encountered.
	
	320    The job encountered an error trying to execute a query and there
	      forecannot generate the list of target workstations for the job.
	      Possible causes are: SQL server is not available; or a fatal low-
	      memory condition was encountered.
	
	321    The job encountered an error trying to reach the Job Details table
	      and therefore cannot generate the list of target workstations for
	      the job. Possible causes are: SQL Server is not started; SQL Server
	      logon account is invalid; a named-pipe connection to the server
	      running SQLServer cannot be established; or the maximum user
	      connections for SQL Server has been reached.
	
	322    The job encountered an error trying to insert a record into the Job
	      Details table and therefore cannot generate the list of target
	      workstations for the job. Possible causes are: SQL server is not
	      available.
	
	323    The job has been failed without performing any actions, because the
	      generated list of target workstations was empty. The provided query,
	      machine group, or machine path, along with any site limiting,
	      resulted in zero machines being targeted. Therefore, the job has
	      nothing to do.
	
	324    The job encountered an error trying to generate the list of
	      destination sites. Possible causes are: SQL server is not available.
	
	325    The job encountered an error trying to reach the Requests table and
	      therefore cannot be activated. Possible causes are: SQL Server is
	      not started; SQL Server logon account is invalid; a named-pipe
	      connection to the server running SQL Server cannot be established;
	      or the maximum user connections for SQL Server has been reached.
	
	326    The job encountered an error trying to insert a record into the
	      Requests table and therefore cannot be activated. Possible causes
	      are: SQL server is not available.
	
	327    The job encountered an error trying to connect to the registry while
	      updating job status. Job status updating will be skipped for this
	      cycle.
	
	328    The job encountered an error trying to read the registry while
	      updating job status. Job status updating will be skipped for this
	      cycle.
	
	329    An error occured while trying to compress the contents of the source
	      directory specified for the workstation version of the package.
	      Possible causes are:  the source directory specified is invalid or
	      cannot be accessed by the compression process;  or, there was
	      insufficient disk space to compress the contents of the source
	      directory.
	
	330    An error occured while trying to compress the contents of the source
	      directory specified for the server version of the package. Possible
	      causes are: the source directory specified is invalid or cannot be
	      accessed by the compression process; or, there was insufficient disk
	      space to compress the contents of the source directory.
	
	331    An error occured while trying to compress the source directory or
	      file associated with the job. Possible causes are: the source
	      directory or file does not exist orcannot be accessed by the
	      compression process; or, there was insufficient disk space to
	      compress the contents of the source directory or file.
	
	332    The system cannot find any defined addresses by which this site can
	      send to a destination site for the job. Possible causes are: no
	      addresses have been defined between this site and the destination
	      site; the SMS site server registry (which holds the address list) is
	      not active and on the network; or, SMS_SCHEDULER does not have
	      sufficient rights to access the SMS site server registry.
	
	333    Cannot read registry on Server X. Check for missing SMS keys in
	      registry.
	
	334    Cannot update Site Table for site X. Check Sites table and SQL
	      Server.
	
	335    First config job created for site X. %5
	
	336    Cannot read Site Control file for site X from database on SQL
	      Server Y. Check SQL Server and Site Control table.
	
	337    Cannot write Site Control file for site X to database on SQL Server
	      Y. Check SQL Server and Site Control table.
	
	338    Cannot write Site Control file to the SITE.SRV\SITECFG.BOX. Check
	      for directory existence.
	
	339    Site Control file X has bad or unknown type. Check for corrupted
	      file.
	
	340    Cannot read the Site Control file X. Check for locked or corrupted
	      file.
	
	341    Site X had bad or unknown status value in Sites table. Check SQL
	      Tables.
	
	342    Cannot change to working directory X. Check for directory existence.
	
	343    Cannot connect to Job Source [SQL]. Check SQL Server and Jobs table.
	
	344    Cannot insert a job into Job Source [SQL]. Check SQLServer and Jobs
	      table.
	
	345    Cannot read Job X from SQL tables. Check SQLServer and Jobs table.
	
	346    Cannot generate a new send request for remote site intallation.
	
	347    No address is available to reach site X. Cannot create a job.
	
	348    Remote site install package created. X files copied to make package.
	
	349    Remote site installation sequence started for site X.
	
	Additional query words: sms prodsms
	
	======================================================================
	Keywords          : kbnetwork kbDatabase kbScheduler smsdatabase smsscheduler 
	Technology        : kbSMSSearch kbSMS100 kbSMS110
	Version           : :1.0,1.1
	
	=============================================================================
	

{% endraw %}
