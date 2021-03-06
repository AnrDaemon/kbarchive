---
layout: page
title: "Q169892: Host Print Transform Can Now Be Configured by SNA Server"
permalink: /kb/169/Q169892/
---

## Q169892: Host Print Transform Can Now Be Configured by SNA Server

{% raw %}

	Article: Q169892
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The existing 5250 print service only supports 5224 print devices. This article
	discusses several ways that you can use more advanced printing features,
	including the new functionality in Microsoft SNA Server version 3.0 Service Pack
	2 (SP2).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	This problem has been added in the latest SNA Server version 3.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	If a print application requires more advanced printing features, (such as those
	supported by a 3812 printer) the AS/400 administrator can manually configure the
	printer device for Host Print Transform (HPT) on the AS/400. Because a 3812
	device has more functionality than a 5224 device, some AS/400 applications that
	rely on 3812 functionality may experience reduction of functionality or even be
	unable to exercise any print function through a 5224 device.
	
	Microsoft has extended the print server functionality to 3812 devices by enabling
	HPT through the startup of a passthrough session. In this case, SNA Print
	Service is relying on the AS/400 to format the print data. For an AS/400 system
	with V2R3 or a later OS, there is an additional field Q (0xd8) in the Program
	Initialization Parameters (PIP) that can be used to enable HPT support
	automatically. The Q field also allows you to configure a number of features
	that you can take advantage of in Microsoft SNA Server.
	
	There is now a way for SNA Server Print Service to automatically enable and
	configure various Host Print Transform parameters using an updated version of
	the SNA Server 3.0 (post-sp1) command line utility Snacfg.exe. This is enabled
	by using the Q field (0xD8) in the PIP data inside the FMH-5 Attach message.
	
	NOTE: Refer to the "Host Print Service and AS/400 Configuration" section of the
	SNA Server Service Pack 1 Release Notes if you want to manually enable Host
	Print Transform on the AS/400.
	
	To see all of the Host Print Transform options, type:
	
	  "C:> SNACFG PRINTSESSIONONAPPC /?" (without the quotation marks)
	
	The syntax of this command is:
	
	  SNACFG PRINTSESSIONAPPC /LIST
	  SNACFG PRINTSESSIONAPPC printsessionappcname
	  SNACFG PRINTSESSIONAPPC printsessionappcname /PRINT
	  SNACFG PRINTSESSIONAPPC printsessionappcname /ADD [options]
	  SNACFG PRINTSESSIONAPPC printsessionappcname [options]
	  SNACFG PRINTSESSIONAPPC printsessionappcname /DELETE
	
	Available options are:
	
	...
	  <other options>
	...
	  /HOSTPRINTTRANSFORM:{ Yes | No }
	  /FONTID:text
	  /MSGQNAME:text
	  /MSGLIBNAME:text
	  /FORMFEED:{ Continuous | Cut | AutoCut }
	  /HOSTPRINTERTYPE:text
	  /PAPERSRC1:{ Default | Letter | Legal | Executive | A4 | A5 | B5 |
	     CONT80 | CONT132 | None }
	  /PAPERSRC2:{ Default | Letter | Legal | Executive | A4 | A5 | B5 | None
	     }
	  /ENVELOPESRC:{ Default | Monarch | NUM9 | NUM10 | B5 | C5 | DL | None }
	  /CODEPAGE899:{ Yes | No }
	  /SPECIALOBJ:text
	  /SPECIALLIB:text
	  /DEVICETYPE:{ 5224 | 3812 }
	
	Features Supported by Additional Field Q in PIP Data
	----------------------------------------------------
	
	There are a number of features you can control through the Q field of the PIP, as
	listed below:
	
	- Host Print Transform - Enable Host Print Transform. The default is: YES.
	
	- Font ID - specify the Font Identifier used by 3812, 3816, and 5219, and IPDS
	  printers. It can be 3-, 4-, and 5- digits. The user must check with the
	  printer manual for this font number. The default is: 11.
	
	- Message Queue Name - Specify the name of the message queue to which device
	  operational messages are sent. The default is: QSYSOPR.
	
	- Message Lib Name: Specify the name of the library where the message queue is
	  located. The default is: *LIBL.
	
	- Form Feed - Specify Form Feed method. The default is: Continuous.
	
	- Printer Type and Model - The type and model of the printer driver rendering
	  the job.
	
	- Paper Source 1 - Specify the size of the paper in Paper Source 1. The default
	  is: 0x01 Letter.
	
	- Paper Source 2 - Specify the size of the paper in Paper Source 2. The default
	  is: 0x01 Letter.
	
	- Envelope Source - Specify the size of the envelope. The default is: 0x0a
	  (NUMBER10)
	
	- ASCII Code Page 899 Support - Specify whether the printer has Code Page 899
	  Installed. The default is: NO.
	
	- Customizing Library Name - This field is blank if a manufacturer Printer Type
	  and Model are specified. The default is: BLANK.
	
	- Customizing Object Name - This field is blank if a manufacturer Printer Type
	  and Model are specified. The default is: BLANK.
	
	- Device Type - The default is: 3812.
	
	Configuration Parameters
	------------------------
	
	Possible Values for Font ID: 1- 299
	
	Possible values for Printer Type are found using the CHGDEVPRT command on the
	AS/400. An example would be *HP560C.
	
	Supported AS/400 printers include the following:
	
	  Compaq PageMaker 15 (HP Mode)
	  Compaq PageMaker 20 (HP Mode)
	  Epson ActionPrinter 2250
	  Epson ActionPrinter 3250
	  Epson ActionPrinter 5000
	  Epson ActionPrinter 5500
	  Epson DFX-5000
	  Epson DFX-8000
	  Epson FX-850
	  Epson FX-870
	  Epson FX-1170
	  Epson LX-810
	  Epson LQ-510
	  Epson LQ-570
	  Epson LQ-860
	  Epson LQ-870
	  Epson LQ-1070
	  Epson LQ-1170
	  Epson LQ-2550
	  Epson SQ-870
	  Epson SQ-1170
	  Epson EPL-7000
	  Epson EPL-8000
	  HP LaserJet Series II
	  HP LaserJet IID
	  HP LaserJet IIP
	  HP LaserJet III
	  HP LaserJet IIID
	  HP LaserJet IIIP
	  HP LaserJet IIISI
	  HP LaserJet 4
	  HP LaserJet 310 (Black Printer Only)
	  HP LaserJet 500
	  HP LaserJet 520
	  HP LaserJet 550C
	  HP LaserJet 560C
	  HP PaintJet
	  HP PaintJet XL
	  HP PaintJet XL 300
	  IBM 2380 Personal Printer Series II
	  IBM 2381 Personal Printer Series II
	  IBM 2390 Personal Printer Series II
	  IBM 2391 Personal Printer Series II
	  IBM 3812 Pageprinter
	  IBM 3816 Pageprinter
	  IBM 3812 Page Printer (HP Mode)
	  IBM 3816 Page Printer (HP Mode)
	  IBM 39302 IBM 3930-02S Page Printer
	  IBM 39302 IBM 3930-02D Page Printer
	  IBM 39303 IBM 3930-03S Page Printer
	  IBM 39303 IBM 3930-03D Page Printer
	  IBM 4019 LaserPrinter
	  IBM 4019 LaserPrinter (HP Mode)
	  IBM 4019E LaserPrinter E
	  IBM 4019E LaserPrinter E(HP Mode)
	  IBM 4029-010 LaserPrinter 5E
	  IBM 4029-010 LaserPrinter 5E(HP Mode)
	  IBM 4029-020 LaserPrinter 6
	  IBM 4029-020 LaserPrinter 6 (HP Mode)
	  IBM 4029-030 LaserPrinter 10
	  IBM 4029-030 LaserPrinter 10(HP Mode)
	  IBM 4029-040 LaserPrinter 10L
	  IBM 4029-040 LaserPrinter 10L(HP Mode)
	  IBM 4037 5E Printer
	  IBM LaserPrinter 4039-10D (HP Mode)
	  IBM LaserPrinter 4039-10D Plus (HP Mode)
	  IBM LaserPrinter 4039-10R (HP Mode)
	  IBM LaserPrinter 4039-10R Plus(HP Mode)
	  IBM LaserPrinter 4039-12R (HP Mode)
	  IBM LaserPrinter 4039-12R Plus(HP Mode)
	  IBM LaserPrinter 4039-12L(HP Mode)
	  IBM LaserPrinter 4039-12L Plus(HP Mode)
	  IBM LaserPrinter 4039-16L(HP Mode)
	  IBM LaserPrinter 4039-16L Plus(HP Mode)
	  IBM 4070 IJ
	  IBM 4070 IJ(Epson Mode)
	  IBM 4072 Execjet
	  IBM 4072 Execjet* II Printer(HP Mode)
	  IBM 4201-1 Proprinter
	  IBM 4201-2 Proprinter II
	  IBM 4201-3 Proprinter III
	  IBM 4202-1 Proprinter Printer XL
	  IBM 4202-2 Proprinter II XL
	  IBM 4202-3 Proprinter III XL
	  IBM 4207-1 Proprinter X24
	  IBM 4207-2 Proprinter X24E
	  IBM 4208-1 Proprinter XL24
	  IBM 4208-2 Proprinter XL24E
	  IBM 4212 Proprinter 24P
	  IBM 4216-10 Personal Pageprinter
	  IBM 4226-302 Printer
	  IBM 4230-4S3 Printer(IBM Mode)
	  IBM 4230-413 Printer(IBM Mode)
	  IBM 4232-302 Printer(IBM Mode)
	  IBM 4712-1 Transaction Printer
	  IBM 4712-2 Transaction Printer
	  IBM 4722-1 Docoument Printer
	  IBM 4712-2 Docoument Printer
	  IBM 4770 InkJet Transaction Printer
	  IBM 5152 Graphics Printer
	  IBM 5201-2 QuietWriter
	  IBM 5202-1 QuietWriter III
	  IBM 5204-1 QuietWriter
	  IBM 5216 WheelPrinter
	  IBM 6408-A00 Printer (IBM Mode)
	  IBM 6408-CTA Printer (IBM Mode)
	  IBM 6412-A00 Printer (IBM Mode)
	  IBM 6412-CTA Printer (IBM Mode)
	  NEC P2 PinWriter
	  NEC P2200 PinWriter
	  NEC P2200XE PinWriter
	  NEC P5200 PinWriter
	  NEC P5300 PinWriter
	  NEC P6200 PinWriter
	  NEC P6300 PinWriter
	  Okidata Microline 184 Turbo (IBM Mode)
	  Okidata Microline 320 (IBM Mode)
	  Okidata Microline 321 (IBM Mode)
	  Okidata Microline 390 Plus (IBM Mode)
	  Okidata Microline 391 Plus (IBM Mode)
	  Okidata Microline 393 Plus (IBM Mode)
	  Okidata Microline 590 (IBM Mode)
	  Okidata Microline 591 (IBM Mode)
	  Okidata OL400 LED Page Printer
	  Okidata OL800 LED Page Printer
	  Okidata OL810 LED Page Printer
	  Okidata OL820 LED Page Printer
	  Okidata Pace mark 3410
	  Panasonic KX-P1123(Epson Mode)
	  Panasonic KX-P1124(Epson Mode)
	  Panasonic KX-P1124i(Epson Mode)
	  Panasonic KX-P1180(Epson Mode)
	  Panasonic KX-P1180i(Epson Mode)
	  Panasonic KX-P1191(Epson Mode)
	  Panasonic KX-P1624(Epson Mode)
	  Panasonic KX-P1654(Epson Mode)
	  Panasonic KX-P1695(Epson Mode)
	  Panasonic KX-P2123(Epson Mode)
	  Panasonic KX-P2124(Epson Mode)
	  Panasonic KX-P2180(Epson Mode)
	  Panasonic KX-P2624(Epson Mode)
	  Panasonic KX-P4410(Epson Mode)
	  Panasonic KX-P4420(Epson Mode)
	  Panasonic KX-P4430(Epson Mode)
	  Panasonic KX-P4450i(Epson Mode)
	  Panasonic KX-P4451(Epson Mode)
	  Xerox 4215/MRP(HP Mode)
	  Xerox 4219/MRP(HP Mode)
	  Xerox 4220/MRP(HP Mode)
	  Xerox 4235 Laser Printing (HP Mode)
	  Xerox 4700 II Color Document Printer (HP Mode)
	  Select Customized Object
	  Customizing Object QWPDEFAULT
	  Customizing Library *LIBL
	
	Possible Values for Paper Source 1
	
	  Default    (0x00)
	  Letter (8.5 x 11 inches)  (0x01)
	  Legal (8.5 x 14 inches)  (0x02)
	  Executive( 7.25 X 10.5 inches) (0x03)
	  A4 (210 x 297 mm)  (0x04)
	  A5 (148 x 210 mm)  (0x05)
	  B5 (182 x 257 mm)  (0x06)
	  Continuous Form ( 8.0 inches) (0x07)
	  Continuous Form (13.2 inches) (0x08)
	  None    (0xff)
	
	Possible Values for Paper Source 2
	
	  Default    (0x00)
	  Letter (8.5 x 11 inches)  (0x01)
	  Legal (8.5 x 14 inches)  (0x02)
	  Executive( 7.25 X 10.5 inches) (0x03)
	  A4 (210 x 297 mm)  (0x04)
	  A5 (148 x 210 mm)  (0x05)
	  B5 (182 x 257 mm)  (0x06)
	  None    (0xff)
	
	Possible Values for Envelope Source
	
	  Default    (0x00)
	  Monarch (3.875 x 7.5 inches) (0x06)
	  Number 9 ( 3.875 x 8.875 inches) (0x09)
	  Number 10 (4.125 x 9.5 inches) (0x0a)
	  B5 (176 x 250 mm)  (0x0b)
	  C5 (162 x 229 mm)  (0x0c)
	  DL (110 x 220 mm)  (0x0d)
	  None    (0xff)
	
	Error Handling:
	
	If the AS/400 target system is unable to supported the Q Field in the PIP data,
	or there is any error in the parameters, the 5250 print service will generate an
	event log and indicates inactive state for the corresponding service.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300SP1
	Version           : WINDOWS:3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
