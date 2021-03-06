---
layout: page
title: "Q128591: Encarta Err Msg: MindMaze Cannot Play Game Music"
permalink: /kb/128/Q128591/
---

## Q128591: Encarta Err Msg: MindMaze Cannot Play Game Music

{% raw %}

	Article: Q128591
	Product(s): Microsoft Home Kids Products
	Version(s): 1995 edition
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsound kbimukbfaq
	Last Modified: 09-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta for Windows 1995 edition 
	- Microsoft Encarta 96 Encyclopedia for Windows 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- Microsoft Encarta 98 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 99 
	- Microsoft Encarta Reference Suite 99 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to play MindMaze in Microsoft Encarta, you may receive the
	following error message:
	
	  MindMaze cannot play game music.
	
	CAUSE
	=====
	
	The behavior can occur for either of the following reasons:
	
	- The MIDI (Musical Instrument Digital Interface) settings for your sound card
	  are not properly configured.
	
	- The [mci extensions] section of the Win.ini file is missing or the
	  MID=Sequencer line is not spelled correctly.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods:
	
	Configure the MIDI Settings for Your Sound Card
	-----------------------------------------------
	
	Microsoft Windows 3.0 or later:
	
	To properly configure the MIDI settings for your sound card, follow these steps:
	
	1. Double-click the Main group in Program Manager.
	
	2. Double-click Control Panel, and then double-click MIDI Mapper.
	
	3. Click Setups, and then click Edit.
	
	4. Set the Port Name on Channels 13-16 to match the FM Synthesizer chip on the
	  sound card installed in your computer. The correct entry in the list should
	  contain FM or FM Synth.
	
	5. Click OK. When you are prompted to save the changes, click Yes.
	
	6. Click Close, and then close Control Panel.
	
	Microsoft Windows 95:
	
	If you are using Windows 95, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q138314 Multimedia: General MIDI Troubleshooting for Windows 95
	
	MID=Sequencer Line Is Missing or Not Spelled Correctly
	------------------------------------------------------
	
	Use a text editor such as Notepad or WordPad to make the following changes to the
	Win.ini file located in the Windows folder:
	
	Locate the [mci extensions] section and add the following lines if they are not
	already present:
	
	     WAV=WaveAudio
	     MID=Sequencer
	     RMI=Sequencer
	     AVI=AVIVideo
	     MMM=MMMovie
	
	Make sure the MID=Sequencer line in the [mci extensions] section of the Win.ini
	file is spelled correctly.
	
	If the [mci extensions] section does not exist, create it.
	
	Additional query words: multi multi-media media
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsound kbimu kbfaq
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbEncartaEncycSearch kbEncarta1995 kbEncartaEnCyc1996 kbEncartaEnCyc1997 kbEncartaEnCyc1997Del kbEncartaEnCyc1999 kbEncartaEnCyc1998 kbEncartaReference99
	Version           : :1995 edition
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
