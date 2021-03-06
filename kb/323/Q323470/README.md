---
layout: page
title: "Q323470: HOW TO: Create a Secure WebDAV Publishing Directory"
permalink: /kb/323/Q323470/
---

## Q323470: HOW TO: Create a Secure WebDAV Publishing Directory

{% raw %}

	Article: Q323470
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 21-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Services version 5.1 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Create a WebDAV Publishing Directory
	- Set Up Basic Authentication
	- Troubleshooting
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article describes how to create a secure Web Distributed
	Authoring and Versioning (WebDAV) publishing directory.
	
	Create a WebDAV Publishing Directory
	------------------------------------
	
	1. On the Microsoft Windows 2000 desktop, click My Computer.
	
	2. In the Inetpub directory, create a physical directory. For example, if you
	  name the directory WebDAV, the path to this directory is C:\Inetpub\WebDAV.
	  You can put this directory anywhere except under the Wwwroot directory.
	  Wwwroot is an exception because its default discretionary access control
	  lists (DACLs) are different from those on other directories.
	
	3. Click Start, click Programs, click Administrative Tools, and then open the
	  Internet Information Services (IIS) snap-in. Click to select the Web site in
	  which you want to create the virtual directory, and then map it to the
	  physical directory that you created in step 2.
	
	4. Type "WebDAV" (without the quotation marks) as the alias for this virtual
	  directory, and then link it to the physical directory that you created in
	  step 2.
	
	5. Reset the default NTFS file system permissions to something more restrictive.
	  Users need at least Read permissions to see the directory. If users want to
	  upload content, users also need Write permissions.
	
	6. Grant the Read, Write, and Browsing access permissions for the virtual
	  directory from the IIS Microsoft Management Console (MMC). This grants users
	  the right to publish documents on this virtual directory and to see a list of
	  the files in it. Although Microsoft does not recommend this for security
	  reasons, you can grant the same access to all of your Web site and allow
	  clients to publish to all of your Web server.
	
	  NOTE: Granting Write access does not give a client the ability to modify
	  Active Server Pages (ASP) pages or any other script-mapped files. To allow
	  these files to be modified, you must grant Write permissions and Script
	  source access after you create the virtual directory.
	
	Set Up Basic Authentication
	---------------------------
	
	1. Set up Secure Sockets Layer (SSL).
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q290625 HOWTO: Configure SSL in a Windows 2000 IIS 5.0 Test Environment Using
	  Certificate Server 2.0
	
	2. After you have installed the certificate on the Web server, enable Basic
	  authentication on the WebDAV virtual directory in the IIS MMC:
	
	  a. Click Start, click Programs, and then click Administrative Tools.
	
	  b. Click Internet Information Services. This opens the MMC for IIS.
	
	  c. Locate your WebDAV publishing directory under the Web site that you
	     created. Right-click the directory, and then click Properties.
	
	  d. In the window that appears, click the Directory Security tab. Under
	     Anonymous Access and Authentication Control, click Edit. This opens the
	     Authentication Methods window.
	
	  e. Click to select Basic authentication for the virtual directory. Make sure
	     that nothing except Basic is selected.
	
	  f. Click OK in the next two windows so that the settings take effect.
	
	Troubleshooting
	---------------
	
	For a user to log on to a server using Basic authentication, their user account
	needs Log on locally permissions. You can add these permissions from the Local
	Security Policy.
	
	REFERENCES
	==========
	
	For more information, see the Internet Information Services 5.0 documentation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500 kbiis510
	Version           : :5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
