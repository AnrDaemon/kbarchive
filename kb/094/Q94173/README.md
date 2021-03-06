---
layout: page
title: "Q94173: Incorrect Printer Name in Setup Dialog Box"
permalink: /kb/094/Q94173/
---

## Q94173: Incorrect Printer Name in Setup Dialog Box

{% raw %}

	Article: Q94173
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you modify a printer description in the CONTROL.INF file or the
	[PrinterPorts] section of the WIN.INI file, an incorrect printer name may appear
	in the Setup dialog box of the Control Panel. The name that appears in the Setup
	dialog box varies depending on the printer driver you are using.
	
	MORE INFORMATION
	================
	
	The name of the printer listed in the Installed Printers box is derived from the
	[PrinterPorts] section of WIN.INI. You may want to customize this name to
	provide information about the printer. If you do so, the customized name appears
	in the Installed Printers box; however, customizing the name may cause an
	incorrect printer name to be displayed in the Setup dialog box.
	
	This problem only occurs if you are using either the UNIDRV.DLL or the
	PSCRIPT.DRV driver; it does not occur if you are using the HPPCL5A.DRV driver.
	If you use either UNIDRV.DLL or PSCRIPT.DRV, the customized printer name is
	compared to an internal list of printers. If a match is not found, a default
	printer name is assigned based on the printer driver you are using.
	
	For example, the EPSON9.DRV driver defaults to the printer name Epson MX-80,
	whereas the PSCRIPT.DRV driver defaults to the printer name Apple LaserWriter
	Plus. If a printer name is customized and the printer driver's default printer
	name matches the installed printer, the change works properly.
	
	Another way to customize a printer name is to change the name in the CONTROL.INF
	file. This causes the new name to appear in the "List of Printers" box that you
	get when you choose Add in the "Printers" dialog box. When installed, the
	customized printer name is written to the WIN.INI file and the above problem may
	exist.
	
	The following is a list of printer drivers and the default printer name with
	which they are associated:
	
	  Driver          Default Printer
	  -------------------------------
	
	  CANON10E.DRV    Canon Bubble-Jet BJ-10e
	  CANON130.DRV    Canon Bubble-Jet BJ-130e
	  CANON330.DRV    Canon Bubble-Jet BK-300
	  CITOH.DRV       C-Itoh 8510
	  CIT9US.DRV      Citizen 120D
	  CIT24US.DRV     Citizen PN48
	  DICONIX.DRV     Diconix 150 Plus
	  Epson9.DRV      Epson MX-80
	  Epson24.DRV     Epson LQ-500
	  ESCP2.DRV       Epson LQ-570 ESC /P2
	  EXECJET.DRV     IBM ExecJet
	  FUJI9.DRV       Fujitsu DX 2100
	  FUJI24.DRV      Fujitsu DL 2400
	  HPPCL.DRV       HP LaserJet Series II
	  HPPLOT.DRV      ColorPro
	  HPDSKJET.DRV    HP DeskJet
	  IBM5204.DRV     IBM Quickwriter 5204
	  NEC24PIN.DRV    NEC Pinwriter P2200
	  OKI9IBM.DRV     Okidata Ml 321-IBM
	  OKI9.DRV        Okidata ML 192
	  OKI24.DRV       Okidata ML 380
	  PSCRIPT.DRV     Apple LaserWriter Plus
	  PAINTJET.DRV    HP PaintJet
	  PANSON24.DRV    Panasonic       KX-P1123
	  PANSON9.DRV     Panasonic       KX-P1180
	  PROPRINT.DRV    IBM Proprinter
	  PROPRN24.DRV    IBM Proprinter X24
	  PS1.DRV         IBM PS/1 2205
	  THINKJET.DRV    HP ThinkJet (2225 C-D)
	  TI850.DRV       TI 850/855
	  QWIII.DRV       IBM QuietWriter III
	
	For more information about customizing printer names in Windows, query on the
	following words in the Microsoft Knowledge Base:
	
	  changing and printer and description
	
	Additional query words: 3.10 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
