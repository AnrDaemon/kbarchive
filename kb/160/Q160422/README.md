---
layout: page
title: "Q160422: How IIS Launches a CGI Application"
permalink: /kb/160/Q160422/
---

## Q160422: How IIS Launches a CGI Application

{% raw %}

	Article: Q160422
	Product(s): Internet Information Server
	Version(s): WINNT: 1.0,2.0,3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 1.0, 2.0, 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you access an HTML page, and the anonymous account does not have access to
	the file, the Internet Information Server (IIS) internally reports an error
	message then sends the authentication method selected by the Web Administrator
	(Basic or Windows NT Challenge).
	
	However, CGI/ISAPI works differently. If Allow Anonymous user authentication is
	enabled, and you go to a URL that is protected by a Windows NT (NTFS) partition,
	the server will first try to run the application using the Anonymous account. If
	the account is allowed to run the application via NTFS, then the application
	will run, and the server will send the output to you.
	
	CAUSE
	=====
	
	The problem occurs when the Anonymous account does not have rights to the CGI.
	When you try to launch the CGI application, IIS uses the Anonymous user. Because
	the account does not have rights to the file, the process fails to run and an
	error message is returned via STDOUT.
	
	However, to IIS the process appears to launch and terminate normally. Because the
	Access Denied error message is placed in STDOUT, IIS has no way of knowing that
	the process failed. Therefore, it does not try any other authentication methods
	because the Anonymous account was able to launch the process. IIS uses the
	createprocessasuser API call to launch the CGI application. Createprocessasuser
	will terminate normally if the user does not have NTFS rights to that CGI/ISAPI
	application.
	
	WORKAROUND
	==========
	
	Use one of the following methods:
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	NOTE: The following is the full path to the registry key:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ W3SVC\Parameters
	
	- Modify the registry to run all applications as the system.
	
	  Under the W3SVC/Parameters, place the value CreateProcessAsUser as a REG_DWORD
	  and give it a value of 0. This causes the CGI to be ran with the
	  CreateProcess API and run in the system context. This has serious security
	  implications because CGI scripts will have much greater access to the system
	  than they normally would.
	
	  NOTE: All users would be able to launch CGI no matter what user they are
	  authenticated as.
	
	- You can also run the CGI/ISAPI from a secured web page. If you run it from a
	  secured web page, you will have to either be authenticated by Basic or NT
	  Challenge. When you click the URL for the CGI/ISAPI, it will pass the
	  REMOTE_USER environment variable, and the CreateProcessAsUser API will use
	  that user to run the CGI. Anonymous will not be used in that instance because
	  a user account has already being passed to the server.
	
	- Turn off Anonymous access to the server, and use only Basic or NT Challenge.
	
	Additional query words: iis
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400 kbiis300 kbiis200 kbiis100
	Version           : WINNT: 1.0,2.0,3.0,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
