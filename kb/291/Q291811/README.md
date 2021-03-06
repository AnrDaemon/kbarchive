---
layout: page
title: "Q291811: Game Stops Responding if USB, AGP Card Use Same Port"
permalink: /kb/291/Q291811/
---

## Q291811: Game Stops Responding if USB, AGP Card Use Same Port

{% raw %}

	Article: Q291811
	Product(s): Microsoft Home Games
	Version(s): 1.0,2.0
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Age of Empires II Expansion: The Conquerors 
	- Microsoft Age of Empires II: The Age of Kings, version 2.0 
	- Microsoft Baseball 2001 
	- Microsoft Combat Flight Simulator 2: WWII Pacific Theater, version 1.0 
	- Microsoft Combat Flight Simulator: WWII Europe Series, version 1.0 
	- Microsoft Crimson Skies 
	- Microsoft Flight Simulator 98 
	- Microsoft Flight Simulator 2000 
	- Microsoft MechWarrior 4: Vengeance 
	- Microsoft Metal Gear Solid 
	- Microsoft Midtown Madness 2, version 2.0 
	- Microsoft Motocross Madness 2, version 2.0 
	- Microsoft Monster Truck Madness 2, version 2.0 
	- Microsoft NBA Inside Drive 2000, version 1.0 
	- Microsoft NFL Fever 2000, version 1.0 
	- Microsoft StarLancer, version 1.0 
	- Microsoft Train Simulator, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When starting any of the games listed at the beginning of this article in
	three-dimensional (3-D) mode, the game may stop responding (hang).
	
	CAUSE
	=====
	
	This problem occurs if the Universal Serial Bus (USB) device is using the same
	bus as the Accelerated Graphics Port (AGP) video card.
	
	RESOLUTION
	==========
	
	To resolve this issue, use any of the following methods.
	
	Method 1: Run the game in Software Mode
	---------------------------------------
	
	Configure the 3-D renderer to use Software Rasterization when you start the
	game.
	
	NOTE: If you turned off the 3-D renderer and then began experiencing the problem
	described in the "Symptoms" section, remove and reinstall the game.
	
	Method 2: Disable AGP Texturing in the DirectX Diagnostic Tool
	--------------------------------------------------------------
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "dxdiag" (without the quotation marks), and then click
	  OK.
	
	3. Click the Display tab.
	
	4. Under DirectX Features, next to AGP Texture Acceleration, click Disable.
	
	5. Under AGP Texture, click Disable.
	
	6. When you receive the following warning, click OK:
	
	  This will disable usage of AGP (Acceleration Graphics Port) for all display
	  devices on your system which support it.
	
	7. Click Exit.
	
	Method 3: Change the Adapter Refresh Rate to Optimal or Adapter Default
	-----------------------------------------------------------------------
	
	NOTE: Because there are several versions of Windows, the following steps may be
	different on your computer. If they are, please consult your product
	documentation to complete these steps.
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click the Display icon.
	
	3. Click the Settings tab. Click Advanced.
	
	4. Click the Adapter tab. In the Refresh rate list, select either Optimal or
	  Adapter Default.
	
	5. Click OK. Click OK again.
	
	6. Click Yes to accept the changes.
	
	7. Click OK.
	
	Additional query words: hangs freeze freezes shuts down stops halts
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbGamesSearch kbFlightSimSearch kbNFLFever2000 kbNFLSearch kbMetalGearSearch kbMotocrossSearch kbStarlancerSearch kbCrimsonSkiesSearch kbBaseballSearch kbMidtownMadSearch kbMonsterTMSearch kbAOESearch kbStarlancer kbMonsterTM2 kbAOE2ExpConquerors kbAOE2Kings kbBaseBall2001 kbCombatFlightSim2 kbCombatFlightSim kbCombatFlightSimSearch kbFlightSim2000 kbFlightSim98 kbMetalGearSolid kbMidtownMadness2 kbMotocrossM2 kbCrimsonSkies kbNBAInsideDrive2000 kbTrainSim
	Version           : :1.0,2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
