---
layout: page
title: "Q258496: Games: How to Troubleshoot Setup Problems in Microsoft Games"
permalink: /kb/258/Q258496/
---

## Q258496: Games: How to Troubleshoot Setup Problems in Microsoft Games

{% raw %}

	Article: Q258496
	Product(s): Microsoft Home Games
	Version(s): 1.0,2.0
	Operating System(s): 
	Keyword(s): kbenv kbsetup fsim kbimu msgame
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Combat Flight Simulator 2: WWII Pacific Theater, version 1.0 
	- Microsoft Combat Flight Simulator: WWII Europe Series, version 1.0 
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	- Microsoft Flight Simulator 2002 
	- Microsoft Flight Simulator 2002 Professional Edition 
	- Microsoft MechWarrior 4: Black Knight 
	- Microsoft MechWarrior 4: Vengeance 
	- Microsoft Motocross Madness 2, version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discribes how to perform basic troubleshooting for problems that
	you may experience when you install Microsoft games.
	
	MORE INFORMATION
	================
	
	To troubleshoot the game problems, use the following methods in the order in
	which they are presented.
	
	Clean the CD-ROM
	----------------
	
	Clean the game CD-ROM to remove dust, smudges, and fingerprints. To do this, use
	a CD-ROM cleaning kit, or gently wipe the silver side of the CD-ROM with a soft,
	lint-free cotton cloth. Do not use paper cloth which can scratch the plastic and
	leave streaks. When you clean the CD-ROM, wipe from the center of the disc
	outward. Do not use a circular motion.
	
	Quit Unnecessary Programs
	-------------------------
	
	Before you install the game, quit any unnecessary programs that are running on
	your computer:
	
	1. On the Windows taskbar, right-click the button for a program, and then click
	  Close.
	
	  Repeat this step to for each button on the Windows task bar.
	
	2. Disable any anti-virus or disk management programs that are installed on the
	  computer. For information about how to disable these programs, see the
	  printed or online documentation for the program.
	
	3. Press CTRL+ALT+DELETE.
	
	4. In the Close Program dialog box, click any program except Explorer or Systray
	  (which are components of Microsoft Windows), and then click End Task.
	
	  If you receive a message which states that the program is busy or not
	  responding, click End Task again.
	
	5. Repeat steps 3 and 4 to quit all programs except Explorer and Systray.
	
	Disable Auto Insert Notification
	--------------------------------
	
	NOTE: If you disable Auto Insert Notification, your programs no longer start
	automatically when you insert the CD-ROM for a program into the CD-ROM drive.
	
	To disable Auto Insert Notification:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. On the Device Manager tab, click the PLUS SIGN (+) next to CDROM to expand
	  the branch.
	
	4. Under the CDROM branch, click your CD-ROM drive, and then click Properties.
	
	5. On the Settings tab, click to clear the "Auto insert notification" check box,
	  click to clear the DMA check box (if available), and then click OK.
	
	6. Click Close.
	
	7. If you are prompted to restart the computer, click Yes.
	
	  If you are not prompted to restart the computer, close Control Panel, and then
	  restart the computer.
	
	Adjust the CD-ROM Cache Settings
	--------------------------------
	
	For additional information about how to adjust CD-ROM cache settings, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q184410 How to Use Msinfo32.exe to Optimize CD-ROM Cache Settings
	
	Check the Temp Folder
	---------------------
	
	To check the Temp folder:
	
	1. Click Start, point to Programs, and then click MS-DOS Prompt.
	
	2. At the command prompt, type "set" (without the quotation marks), and then
	  press ENTER.
	
	3. Make sure that the path on the "TEMP=" line is a valid, fully defined path.
	  By default, the TEMP environment variable contains the following path:
	
	  <drive>:\<windows>\Temp
	
	  where <drive> is the drive letter of the hard disk on which Microsoft
	  Windows is installed, and <windows>is the folder in which Windows is
	  installed.
	
	  NOTE: The following paths are not valid values for the TEMP environment
	  variable:
	
	   - \Windows\temp
	   - Windows\temp
	
	4. Make sure that the Temp folder exists. To do this, type the following lines
	  at the command prompt, pressing ENTER after you type each line
	
	  <drive>:
	  cd \<path>
	
	  where <drive> is the drive letter in the path on the "TEMP=" line, and
	  <path> is the folder path on the "TEMP=" line.
	
	5. If you move to the Temp folder successfully, proceed to the next step.
	
	  If you receive a message stating that the Temp folder does not exist:
	
	  a. Type the following lines at the command prompt, pressing ENTER after you
	     type each line:
	
	  <drive>:
	  cd \<windows>
	  cd temp
	
	     where <drive> is the drive letter of the hard disk on which Windows
	     is installed, <windows> is the folder in which Windows is
	     installed.
	
	     NOTE: If you receive a message stating that the Temp folder does not exist,
	     type the following lines at the command prompt, pressing ENTER after you
	     type each line:
	
	  md Temp
	  cd Temp
	
	  b. At the command prompt, type the following lines, pressing ENTER after you
	     type each line:
	
	  cd \
	  edit autoexec.bat
	
	  c. Use the DOWN ARROW key to move your text cursor to the beginning of the
	     SET TEMP= line in the Autoexec.bat file.
	
	  d. Type "REM" (without the quotation marks), press the SPACEBAR, press the
	     END key, and then press ENTER.
	
	  e. Type the following line
	
	  SET TEMP=<drive>:\<windows>\Temp
	
	     where <drive> is the drive letter of the hard disk on which Windows
	     is installed, <windows> is the folder in which Windows is installed.
	
	  f. Press ALT+F, and then press X.
	
	     When you are prompted to save the changes, press Y.
	
	6. At the command prompt, type "exit" (without the quotation marks), and then
	  press ENTER to return to Windows.
	
	7. If you made any changes, restart the computer.
	
	Empty the Temp folder
	---------------------
	
	To empty the Temp folder, use the appropriate method for your version of
	Windows.
	
	Windows 95:
	
	1. Click Start, and then click Shut Down.
	
	2. Click "Restart in MS-DOS mode", and then click OK.
	
	3. At the command prompt, type the following lines, pressing ENTER after you
	  type each line:
	
	  <drive>:
	  cd \<path>
	
	  where <drive> is the drive letter in the path on the "TEMP=" line, and
	  <path> is the folder path on the "TEMP=" line.
	
	4. At the command prompt, type "del *.tmp" (without the quotation marks), press
	  ENTER, and then press Y.
	
	5. At the command prompt, type "exit" (without the quotation marks), and then
	  press ENTER to restart the computer.
	
	Windows 98:
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click Disk Cleanup.
	
	2. In the Drives box, click the hard disk on which the Temp folder is stored,
	  and then click OK.
	
	3. In the "Files to delete" box, click to select the "Temporary files" check
	  box.
	
	4. Click to clear the check boxes for any files that you do not want to delete,
	  click OK, and then click Yes.
	
	Check for Real Mode (16-bit) CD-ROM Drivers
	-------------------------------------------
	
	Make sure that you are not using a real mode (16-bit) driver for your CD-ROM
	drive. The games requires a protected mode (32-bit) CD-ROM driver.
	
	To determine if a real mode (16-bit) CD-ROM driver is installed instead of a
	protected mode (32-bit) CD-ROM driver:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Device Manager tab.
	
	4. Locate the CDROM branch.
	
	  If the CDROM branch does not exist, your CD-ROM drive uses a real mode CD-ROM
	  driver.
	
	5. Click OK, and then close Control Panel.
	
	To determine if a real mode CD-ROM driver is installed in addition to a protected
	mode CD-ROM driver, examine the Autoexec.bat file for a line that refers to the
	Mscdex.exe file:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "sysedit" (without the quotation marks), and then click
	  OK.
	
	3. In the Autoexec.bat window, look for any lines that refer to the Mscdex.exe
	  file.
	
	If a line that refers to the Mscdex.exe file exists, a real mode CD-ROM driver is
	probably installed on your computer. Contact the manufacturer of your CD-ROM
	drive for information about how to remove the real-mode driver for your CD-ROM
	drive.
	
	If a line that refers to the Mscdex.exe file does not exist, contact the
	manufacturer of your CD-ROM drive to inquire about how to verify that the CD-ROM
	drive is installed corretly, and to inquire about how to obtain and install the
	latest version of the protected mode (32-bit) Windows 95/98 CD-ROM driver for
	your CD-ROM drive.
	
	For information about how to contact the manufacturer of your CD-ROM drive, click
	the appropriate article number in the following list to view the article in the
	Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	Check for Duplicate CD-ROM Drives
	---------------------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. On the Device Manager tab, click the PLUS SIGN (+) next to CDROM to expand
	  the branch.
	
	4. In the CDROM branch, click your CD-ROM drive, and then click Properties.
	
	5. Record the device information and settings on each tab in the device
	  properties dialog box, and then click OK.
	
	6. Repeat steps 4 and 5 for each device in the CDROM branch.
	
	7. Click OK.
	
	8. Close Control Panel.
	
	9. Restart the computer in Safe mode. To do this, use the appropriate method for
	  your version of Microsoft Windows.
	
	  Windows 95:
	
	  Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then select Safe Mode from the Startup menu.
	
	  Windows 98:
	
	  Restart the computer, press and hold down the CTRL key after your computer
	  completes the Power On Self Test (POST), and then select Safe Mode from the
	  Startup menu.
	
	10. Click Start, point to Settings, and then click Control Panel.
	
	11. Double-click System.
	
	12. On the Device Manager tab, click the PLUS SIGN (+) next to CDROM to expand
	  the branch.
	
	13. Verify that there are no changes in the list of devices in the CDROM
	  branch.
	
	  If a new device appears in the branch that did not appear in the list of
	  devices that you noted in steps 4 and 5, click the new device, and then
	  click Remove. Repeat this step for each device in the branch that did not
	  appear in the list that you noted in steps 4 and 5.
	
	  NOTE: If you see new copies of a device that appeared in the list that you
	  noted in steps 4 and 5, check the properties for each copy of the device. If
	  the properties for the device match the properties that you recorded, keep
	  the device. If the properties for the device do not match the properties
	  that you recorded, remove the device.
	
	14. Click OK.
	
	15. When you are prompted to restart the computer, click OK.
	
	Additional query words: msgame flightsim fsim fs2000 fs2k install setup cd fs2002
	
	======================================================================
	Keywords          : kbenv kbsetup fsim kbimu msgame 
	Technology        : _IKkbbogus kbGamesSearch kbFlightSimSearch kbMotocrossSearch kbCombatFlightSim2 kbCombatFlightSim kbCombatFlightSimSearch kbFlightSim2000 kbMotocrossM2 kbFlightSim2002 kbFlightSim2002Pro kbSimSearch
	Version           : :1.0,2.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
