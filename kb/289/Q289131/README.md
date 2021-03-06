---
layout: page
title: "Q289131: Redirect URL Corruption When Requested URL Contains Trailing &quot;/&quot;"
permalink: /kb/289/Q289131/
---

## Q289131: Redirect URL Corruption When Requested URL Contains Trailing &quot;/&quot;

{% raw %}

	Article: Q289131
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbCOMIS kbWin2000sp3fix
	Last Modified: 15-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the HTTP redirect option for virtual directories in Microsoft
	Internet Information Server (IIS) 5.0, HTTP clients may randomly redirect to
	non-existent files, which results in HTTP 404 errors on the client.
	
	CAUSE
	=====
	
	This problem occurs because IIS 5.0 stores an invalid string length for the
	redirected virtual directory source path, which results in corrupted redirects
	when the requested file is concatenated with the source string. The string
	length is stored incorrectly because the initial HTTP client request (which is
	used to set up the redirection cache blob for a redirected virtual directory)
	contains an additional terminating forward slash ("/").
	
	WORKAROUND
	==========
	
	To work around this problem, do not use a terminating forward slash in the
	source for HTML elements that request a file from a redirected virtual directory
	on the IIS 5.0 server. For example, replace the following redirect source path
	
	  http://server/redirected_directory/
	
	with this source path:
	
	  http://server/redirected_directory
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, click the following article number to view the article
	in the Microsoft Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time    Version        Size     File name   Platform
	  -------------------------------------------------------------
	  3/19/2001  05:41p  5.0.2195.3390  357,648  W3svc.dll   i386
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Internet Information Server
	5.0. This problem was first corrected in Windows 2000 Service Pack 3.
	
	Additional query words: kbIISCom
	
	======================================================================
	Keywords          : kbCOMIS kbWin2000sp3fix 
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
