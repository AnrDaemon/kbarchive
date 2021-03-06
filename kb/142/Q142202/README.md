---
layout: page
title: "Q142202: HOWTO: Create a Progress Bar on the Status Bar"
permalink: /kb/142/Q142202/
---

## Q142202: HOWTO: Create a Progress Bar on the Status Bar

{% raw %}

	Article: Q142202
	Product(s): Microsoft C Compiler
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbMFC _IK11590 kbStatBar KbUIDesign kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL kbMFCCtrlBar
	Last Modified: 29-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, version 4.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There are times when you may want to show the progress of a process on the
	status bar. Developer Studio does this when loading a project. You can implement
	this by using CStatusBar and CProgressCtrl.
	
	MORE INFORMATION
	================
	
	A default AppWizard-generated MFC application has a class (CMainFrame) that
	contains a member variable m_wndStatusBar of type CStatusBar. The following
	sample code uses this member variable as the parent of a CProgressCtrl, which
	will be positioned over the first pane of m_wndStatusBar. First, the
	CProgressCtrl is created. Then, the sample code simulates a lengthy process
	using the Sleep function in a for loop.
	
	Sample Code
	-----------
	
	     /* Compile options needed: default
	     */ 
	
	     // This is a menu option handler that takes a long period of time
	     void CMainFrame::OnLengthyProcess()
	     {
	         // Create the CProgressCtrl as a child of the status bar positioned
	         // over the first pane.
	
	         RECT rc;
	         m_wndStatusBar.GetItemRect (0, &rc);
	         CProgressCtrl wndProgress;
	         VERIFY (wndProgress.Create(WS_CHILD | WS_VISIBLE, rc,
	                                                 &m_wndStatusBar, 1));
	         wndProgress.SetRange(0, 50);
	         wndProgress.SetStep(1);
	
	         // Perform some lengthy process, simulated here with a for loop
	         // and the Sleep function.
	
	         for(int i=0;i<50;i++)
	         {
	            Sleep(50);
	            wndProgress.StepIt();
	         }
	     }
	
	Additional query words:
	
	======================================================================
	Keywords          : kbMFC _IK11590 kbStatBar KbUIDesign kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL kbMFCCtrlBar 
	Technology        : kbAudDeveloper kbMFC
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
