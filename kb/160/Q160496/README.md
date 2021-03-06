---
layout: page
title: "Q160496: INFO: Files Modified by VC42b Patch - Part 2 of 4"
permalink: /kb/160/Q160496/
---

## Q160496: INFO: Files Modified by VC42b Patch - Part 2 of 4

{% raw %}

	Article: Q160496
	Product(s): Microsoft C Compiler
	Version(s): 4.2
	Operating System(s): 
	Keyword(s): kbenv kbother kbnokeyword kbDAOsearch kbDatabase kbGenInfo kbMFC kbODBC kbVC kbHWx86 kb
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	- Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual C++ 4.2 patch is a technology update that updates the Visual C++ 4.2
	retail installation to work with the final release of the Win32 and ActiveX
	SDKs. In addition, AppWizard, ClassWizard, and BSCMAKE.EXE have also updated.
	There are four self-extracting files available for this patch. These files
	contain different combinations of the patch. You should download the proper
	self-extracting files that best suit your needs.
	
	For more information on how to download the patch, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q156934 PATCH: Visual C++ 4.2b Patch
	
	This article is broken into four parts with different article numbers. Please see
	the REFERENCES section at the end of this article for information on the
	additional parts.
	
	This is Part 2 of 4.
	
	MORE INFORMATION
	================
	
	Below is a list of files with file size, date, time stamps, and version numbers
	(as proper) before and after the patch is applied. This list is based on the
	comprehensive patch extracted from file vc42b.exe.
	
	Files that are modified by other combinations of the patch are also listed below
	without the file information. You should be able to find the file information
	from the ones listed for the comprehensive patch.
	
	VC42B.EXE Patch
	---------------
	
	Files patched by vc42b.rtp in the \msdev directory (continued from Part 1):
	
	- include\rassapi.h
	  (Before) Size:     9,877  Date: 05/06/96  Time: 02:14a
	  (After)           10,573        09/06/96        10:57a
	
	- lib\rassapi.lib
	  (Before) Size:    13,554  Date: 05/06/96  Time: 02:14a
	  (After)           13,554        09/06/96        10:58a
	
	- include\rasshost.h
	  (Before) Size:     4,641  Date: 05/06/96  Time: 02:14a
	  (After)            4,620        09/06/96        10:57a
	
	- include\regstr.h
	  (Before) Size:    52,748  Date: 01/07/96  Time: 07:31p
	  (After)           60,127        09/06/96        10:57a
	
	- include\richedit.h
	  (Before) Size:    26,424  Date: 02/25/96  Time: 05:18p
	  (After)           29,848        09/06/96        10:57a
	
	- include\rpcdce.h
	  (Before) Size:    36,693  Date: 03/10/96  Time: 03:11a
	  (After)           42,018        09/06/96        10:57a
	
	- include\rpcdcep.h
	  (Before) Size:     9,477  Date: 03/05/96  Time: 09:24a
	  (After)            9,678        09/06/96        10:57a
	
	- include\rpcndr.h
	  (Before) Size:    71,789  Date: 03/13/96  Time: 02:47p
	  (After)           76,660        09/06/96        10:57a
	
	- lib\rpcndr.lib
	  (Before) Size:    20,188  Date: 04/01/96  Time: 05:50p
	  (After)           21,158        09/06/96        10:58a
	
	- lib\rpcns4.lib
	  (Before) Size:    57,800  Date: 05/06/96  Time: 02:14a
	  (After)           57,800        09/06/96        10:58a
	
	- include\rpcproxy.h
	  (Before) Size:    16,712  Date: 03/05/96  Time: 09:25a
	  (After)           16,967        09/06/96        10:57a
	
	- lib\rpcrt4.lib
	  (Before) Size:   383,654  Date: 05/06/96  Time: 02:14a
	  (After)          408,848        09/06/96        10:58a
	
	- include\scode.h
	  (Before) Size:       216  Date: 01/07/96  Time: 07:30p
	  (After)              214        09/06/96        10:57a
	
	- include\scrnsave.h
	  (Before) Size:     8,624  Date: 01/07/96  Time: 07:30p
	  (After)            8,622        09/06/96        10:57a
	
	- lib\scrnsave.lib
	  (Before) Size:    33,628  Date: 05/06/96  Time: 02:14a
	  (After)           33,628        09/06/96        10:58a
	
	- include\servprov.h
	  (Before) Size:     4,755  Date: 06/03/96  Time: 01:18p
	  (After)            5,953        09/06/96        10:57a
	
	- include\servprov.idl
	  (Before) Size:     1,697  Date: 03/22/96  Time: 12:08p
	  (After)            2,372        09/06/96        10:57a
	
	- include\setupapi.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:   102,225  Date: 09/06/96  Time: 10:57a
	
	- lib\setupapi.lib
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:   253,596  Date: 09/06/96  Time: 10:58a
	
	- lib\shell32.lib
	  (Before) Size:   806,754  Date: 05/06/96  Time: 02:14a
	  (After)          837,320        09/06/96        10:58a
	
	- include\shlguid.h
	  (Before) Size:     3,163  Date: 05/06/96  Time: 02:14a
	  (After)            4,747        09/06/96        10:57a
	
	- include\shlobj.h
	  (Before) Size:    93,336  Date: 05/06/96  Time: 02:14a
	  (After)           94,740        09/06/96        10:57a
	
	- include\smpab.h
	  (Before) Size:     1,233  Date: 04/08/96  Time: 07:38p
	  (After)            1,233        09/06/96        10:57a
	
	- include\smps.h
	  (Before) Size:     1,892  Date: 04/08/96  Time: 07:38p
	  (After)            1,892        09/06/96        10:57a
	
	- include\smpxp.h
	  (Before) Size:     3,778  Date: 04/08/96  Time: 07:38p
	  (After)            3,778        09/06/96        10:57a
	
	- include\snmp.h
	  (Before) Size:    17,166  Date: 05/06/96  Time: 02:14a
	  (After)           16,987        09/06/96        10:57a
	
	- lib\snmpapi.lib
	  (Before) Size:    37,846  Date: 05/06/96  Time: 02:14a
	  (After)           37,846        09/06/96        10:58a
	
	- include\sporder.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:     1,944  Date: 09/06/96  Time: 10:57a
	
	- lib\sporder.lib
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:     2,082  Date: 09/06/96  Time: 10:58a
	
	- include\storage.h
	  (Before) Size:       437  Date: 01/07/96  Time: 07:31p
	  (After)              435        09/06/96        10:57a
	
	- include\svcguid.h
	  (Before) Size:    15,330  Date: 01/07/96  Time: 07:31p
	  (After)           16,113        09/06/96        10:57a
	
	- include\svrapi.h
	  (Before) Size:    47,005  Date: 01/18/96  Time: 06:56p
	  (After)           47,005        09/06/96        10:57a
	
	- include\tapi.h
	  (Before) Size:   137,069  Date: 03/30/96  Time: 01:23a
	  (After)          150,246        09/06/96        10:57a
	
	- lib\tapi32.lib
	  (Before) Size:   243,646  Date: 05/06/96  Time: 02:14a
	  (After)          294,736        09/06/96        10:59a
	
	- include\tlhelp32.h
	  (Before) Size:     6,068  Date: 01/07/96  Time: 07:31p
	  (After)            6,068        09/06/96        10:57a
	
	- include\tspi.h
	  (Before) Size:    41,899  Date: 05/06/96  Time: 02:14a
	  (After)           41,575        09/06/96        10:57a
	
	- include\unknwn.h
	  (Before) Size:     8,521  Date: 05/06/96  Time: 02:14a
	  (After)            9,289        09/06/96        10:57a
	
	- include\unknwn.idl
	  (Before) Size:     1,901  Date: 01/07/96  Time: 07:31p
	  (After)            2,001        09/06/96        10:57a
	
	- include\urlhlink.h
	  (Before) Size:     4,383  Date: 05/21/96  Time: 06:28p
	  (After)              089        09/06/96        10:57a
	
	- include\urlmon.h
	  (Before) Size:    64,160  Date: 06/03/96  Time: 01:19p
	  (After)           83,404        09/06/96        10:57a
	
	- include\urlmon.idl
	  (Before) Size:    25,508  Date: 05/30/96  Time: 01:59a
	  (After)           38,958        09/06/96        10:57a
	
	- lib\urlmon.lib
	  (Before) Size:    24,486  Date: 05/28/96  Time: 08:58a
	  (After)           42,464        09/06/96        10:59a
	
	- lib\user32.lib
	  (Before) Size:   514,116  Date: 05/06/96  Time: 02:14a
	  (After)          517,018        09/06/96        10:59a
	
	- lib\uuid.lib
	  (Before) Size:    77,862  Date: 06/18/96  Time: 06:30p
	  (After)          261,278        09/06/96        03:53p
	
	- lib\uuid2.lib
	  (Before) Size:    82,408  Date: 05/30/96  Time: 05:53p
	  (After)              378        09/06/96        10:59a
	
	- lib\uuid3.lib
	  (Before) Size:    11,176  Date: 03/08/96  Time: 06:28p
	  (After)              478        09/06/96        10:59a
	
	- include\variant.h
	  (Before) Size:       437  Date: 05/06/96  Time: 02:14a
	  (After)              435        09/06/96        10:57a
	
	- include\vcr.h
	  (Before) Size:    20,052  Date: 01/07/96  Time: 07:31p
	  (After)           20,052        09/06/96        10:57a
	
	- lib\vdmdbg.lib
	  (Before) Size:    19,422  Date: 05/06/96  Time: 02:14a
	  (After)           19,422        09/06/96        10:59a
	
	- lib\version.lib
	  (Before) Size:    14,862  Date: 05/06/96  Time: 02:14a
	  (After)           14,862        09/06/96        10:59a
	
	- include\vfw.h
	  (Before) Size:   139,519  Date: 05/06/96  Time: 02:14a
	  (After)          139,508        09/06/96        10:57a
	
	- lib\vfw32.lib
	  (Before) Size:   122,740  Date: 05/06/96  Time: 02:14a
	  (After)          122,740        09/06/96        10:59a
	
	- lib\webpost.lib
	  (Before) Size:     8,522  Date: 05/08/96  Time: 04:07p
	  (After)            6,528        09/06/96        10:59a
	
	- include\win32.mak
	  (Before) Size:    15,013  Date: 05/06/96  Time: 02:14a
	  (After)           15,011        09/06/96        10:57a
	
	- lib\win32api.csv
	  (Before) Size:   473,515  Date: 05/06/96  Time: 02:14a
	  (After)          790,157        09/06/96        10:59a
	
	- lib\win32spl.lib
	  (Before) Size:    14,344  Date: 05/06/96  Time: 02:14a
	  (After)            4,542        09/06/96        10:59a
	
	- include\winbase.h
	  (Before) Size:   152,446  Date: 04/24/96  Time: 08:00a
	  (After)          154,540        09/06/96        10:57a
	
	- include\wincrypt.h
	  (Before) Size:    12,615  Date: 04/02/96  Time: 12:31p
	  (After)           13,176        09/06/96        10:57a
	
	- include\windef.h
	  (Before) Size:     7,146  Date: 01/07/96  Time: 07:57p
	  (After)            6,760        09/06/96        10:57a
	
	- include\windows.h
	  (Before) Size:     4,806  Date: 01/07/96  Time: 07:57p
	  (After)            4,903        09/06/96        10:57a
	
	- include\windowsx.h
	  (Before) Size:    71,875  Date: 03/25/96  Time: 12:20p
	  (After)           73,255        09/06/96        10:57a
	
	- include\winerror.h
	  (Before) Size:   198,267  Date: 05/30/96  Time: 01:58a
	  (After)          203,050        09/06/96        10:57a
	
	- include\wingdi.h
	  (Before) Size:   147,365  Date: 05/06/96  Time: 02:14a
	  (After)          147,629        09/06/96        10:58a
	
	- include\wininet.h
	  (Before) Size:    74,233  Date: 05/24/96  Time: 10:15a
	  (After)           78,840        09/06/96        10:58a
	
	- lib\wininet.lib
	  (Before) Size:   108,394  Date: 05/28/96  Time: 08:58a
	  (After)          112,308        09/06/96        10:59a
	
	- include\winioctl.h
	  (Before) Size:    28,535  Date: 04/08/96  Time: 12:44p
	  (After)           30,511        09/06/96        10:58a
	
	- lib\winmm.lib
	  (Before) Size:   183,086  Date: 05/06/96  Time: 02:14a
	  (After)          183,086        09/06/96        10:59a
	
	- include\winnetwk.h
	  (Before) Size:    22,695  Date: 05/06/96  Time: 02:14a
	  (After)           22,739        09/06/96        10:58a
	
	- include\winnls.h
	  (Before) Size:    39,325  Date: 03/29/96  Time: 10:03p
	  (After)           39,651        09/06/96        10:58a
	
	- include\winnls32.h
	  (Before) Size:     3,002  Date: 02/14/96  Time: 12:29p
	  (After)            2,972        09/06/96        10:58a
	
	- include\winnt.h
	  (Before) Size:   179,577  Date: 05/06/96  Time: 02:14a
	  (After)          179,078        09/06/96        10:58a
	
	- include\winperf.h
	  (Before) Size:    28,283  Date: 01/07/96  Time: 07:31p
	  (After)           28,279        09/06/96        10:58a
	
	- include\winresrc.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:    53,424  Date: 09/06/96  Time: 10:58a
	
	- include\winsock2.h
	  (Before) Size:    95,748  Date: 05/06/96  Time: 02:14a
	  (After)           93,959        09/06/96        10:58a
	
	- include\winspool.h
	  (Before) Size:    51,513  Date: 03/29/96  Time: 10:02p
	  (After)           52,635        09/06/96        10:58a
	
	- lib\winspool.lib
	  (Before) Size:   127,016  Date: 05/06/96  Time: 02:14a
	  (After)          131,748        09/06/96        10:59a
	
	- lib\winstrm.lib
	  (Before) Size:     7,774  Date: 05/06/96  Time: 02:14a
	  (After)            7,774        09/06/96        10:59a
	
	- include\wintrust.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:    11,053  Date: 09/06/96  Time: 10:58a
	
	- lib\wintrust.lib
	  (Before) Size:     2,058  Date: 02/27/96  Time: 05:02p
	  (After)            4,550        09/06/96        10:59a
	
	- include\winuser.h
	  (Before) Size:   189,481  Date: 05/06/96  Time: 02:14a
	  (After)          192,575        09/06/96        10:58a
	
	- include\wownt16.h
	  (Before) Size:     4,374  Date: 01/07/96  Time: 07:31p
	  (After)            4,380        09/06/96        10:58a
	
	- include\wpapi.h
	  (Before) Size:     2,587  Date: 05/02/96  Time: 05:52p
	  (After)            2,730        09/06/96        10:58a
	
	- include\wpobj.h
	  (Before) Size:     1,713  Date: 04/16/96  Time: 01:25p
	  (After)            1,778        09/06/96        10:58a
	
	- include\wpspi.h
	  (Before) Size:     8,365  Date: 05/02/96  Time: 05:53p
	  (After)            8,411        09/06/96        10:58a
	
	- lib\ws2_32.lib
	  (Before) Size:    94,826  Date: 05/06/96  Time: 02:14a
	  (After)           93,208        09/06/96        10:59a
	
	- include\ws2atm.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:    16,643  Date: 09/06/96  Time: 10:58a
	
	- include\ws2spi.h
	  (Before) Size:    17,490  Date: 05/06/96  Time: 02:14a
	  (After)           18,485        09/06/96        10:58a
	
	- include\ws2tcpip.h
	  (Before)  N/A. This is a newly added file.
	  (After)  Size:     2,611  Date: 09/06/96  Time: 10:58a
	
	- include\wshisotp.h
	  (Before) Size:     3,356  Date: 01/07/96  Time: 07:31p
	  (After)            3,355        09/06/96        10:58a
	
	- include\wsipx.h
	  (Before) Size:     1,943  Date: 01/07/96  Time: 07:31p
	  (After)            1,941        09/06/96        10:58a
	
	- include\wsnwlink.h
	  (Before) Size:     9,317  Date: 01/07/96  Time: 07:31p
	  (After)            9,315        09/06/96        10:58a
	
	- lib\wsock32.lib
	  (Before) Size:    77,258  Date: 05/06/96  Time: 02:14a
	  (After)           61,422        09/06/96        10:59a
	
	- lib\wst.lib
	  (Before) Size:     2,496  Date: 05/06/96  Time: 02:14a
	  (After)            2,496        09/06/96        10:59a
	
	- include\wtypes.h
	  (Before) Size:    28,449  Date: 05/23/96  Time: 05:42p
	  (After)           29,754        09/06/96        10:58a
	
	- include\wtypes.idl
	  (Before) Size:    35,047  Date: 03/13/96  Time: 02:48p
	  (After)           38,273        09/06/96        10:58a
	
	- mfc\include\afxcom_.h
	  (Before) Size:    13,082  Date: 06/06/96  Time: 12:52p
	  (After)           13,121        09/12/96        01:00a
	
	- mfc\include\afxctl.h
	  (Before) Size:    59,606  Date: 06/11/96  Time: 03:54p
	  (After)           59,321        09/12/96        01:00a
	
	- mfc\include\afxdisp.h
	  (Before) Size:    48,910  Date: 06/10/96  Time: 12:55p
	  (After)           49,958        09/12/96        01:00a
	
	- mfc\include\afxdocob.h
	  (Before) Size:    10,668  Date: 06/13/96  Time: 06:59p
	  (After)           10,671        09/12/96        01:00a
	
	- mfc\include\afxinet.h
	  (Before) Size:    18,937  Date: 06/11/96  Time: 06:12p
	  (After)           19,632        09/12/96        01:00a
	
	- mfc\include\afxisapi.h
	  (Before) Size:    18,119  Date: 06/03/96  Time: 01:46p
	  (After)           18,206        09/12/96        01:00a
	
	- mfc\include\afxmsg_.h
	  (Before) Size:    33,434  Date: 06/03/96  Time: 01:46p
	  (After)           33,440        09/12/96        01:00a
	
	- mfc\include\afxole.h
	  (Before) Size:    66,654  Date: 06/12/96  Time: 03:22p
	  (After)           66,855        09/12/96        01:00a
	
	- mfc\include\afxtempl.h
	  (Before) Size:    44,667  Date: 06/03/96  Time: 01:46p
	  (After)           44,669        09/12/96        01:00a
	
	- mfc\include\afxwin.h
	  (Before) Size:   151,029  Date: 06/03/96  Time: 01:46p
	  (After)          151,232        09/12/96        01:00a
	
	- mfc\src\appui2.cpp
	  (Before) Size:     6,983  Date: 06/03/96  Time: 01:59p
	  (After)            6,921        09/12/96        01:07a
	
	- mfc\src\barstat.cpp
	  (Before) Size:    19,075  Date: 10/09/95  Time: 01:28p
	  (After)           19,078        09/12/96        01:07a
	
	- bin\bscmake.exe
	  (Before) Size:   81,408  Date: 02/07/96  Time: 10:37p Version: 4.10.6038
	  (After)          81,408        08/30/96        03:43a          4.20.6164
	
	- mfc\src\ctlconn.cpp
	  (Before) Size:     6,678  Date: 10/23/95  Time: 12:44p
	  (After)            6,678        09/12/96        01:07a
	
	- mfc\src\ctlcore.cpp
	  (Before) Size:    51,690  Date: 06/03/96  Time: 02:00p
	  (After)           51,698        09/12/96        01:07a
	
	- mfc\src\ctldata.cpp
	  (Before) Size:    11,304  Date: 06/03/96  Time: 02:00p
	  (After)           11,342        09/12/96        01:07a
	
	- mfc\src\ctlevent.cpp
	  (Before) Size:    16,543  Date: 06/03/96  Time: 02:00p
	  (After)           16,543        09/12/96        01:07a
	
	- mfc\src\ctlfont.cpp
	  (Before) Size:     6,067  Date: 10/24/95  Time: 04:53p
	  (After)            6,050        09/12/96        01:07a
	
	- mfc\src\ctlinplc.cpp
	  (Before) Size:    15,857  Date: 06/11/96  Time: 11:12a
	  (After)           15,859        09/12/96        01:07a
	
	- mfc\src\ctlobj.cpp
	  (Before) Size:    10,581  Date: 06/03/96  Time: 02:00p
	  (After)           10,696        09/12/96        01:07a
	
	- mfc\src\ctlpict.cpp
	  (Before) Size:     4,710  Date: 10/09/95  Time: 01:27p
	  (After)            4,726        09/12/96        01:07a
	
	- mfc\src\ctlprop.cpp
	  (Before) Size:    37,494  Date: 06/04/96  Time: 01:44p
	  (After)           37,298        09/12/96        01:07a
	
	- mfc\src\ctlpropx.cpp
	  (Before) Size:    29,882  Date: 06/12/96  Time: 03:17p
	  (After)           29,831        09/12/96        01:07a
	
	- mfc\src\ctlpset.cpp
	  (Before) Size:    24,669  Date: 03/01/96  Time: 11:23a
	  (After)           24,683        09/12/96        01:07a
	
	- mfc\src\ctlquick.cpp
	  (Before) Size:     4,011  Date: 06/11/96  Time: 10:42a
	  (After)            4,189        09/12/96        01:07a
	
	- mfc\src\daocore.cpp
	  (Before) Size:   131,376  Date: 05/31/96  Time: 09:26a
	  (After)          131,389        09/12/96        01:07a
	
	- mfc\src\dlgfnt.cpp
	  (Before) Size:     6,936  Date: 04/23/96  Time: 07:23p
	  (After)            6,971        09/12/96        01:07a
	
	- mfc\src\dlgprop.cpp
	  (Before) Size:    31,330  Date: 06/08/96  Time: 01:17p
	  (After)           31,179        09/12/96        01:07a
	
	- mfc\src\dllmodul.cpp
	  (Before) Size:     6,427  Date: 05/14/96  Time: 02:36p
	  (After)            6,431        09/12/96        01:07a
	
	- mfc\lib\eafxis.lib
	  (Before) Size:   112,610  Date: 06/18/96  Time: 06:46p
	  (After)          113,094        09/12/96        01:54a
	
	- mfc\lib\eafxisd.lib
	  (Before) Size:   110,912  Date: 06/18/96  Time: 06:45p
	  (After)          111,338        09/12/96        01:54a
	
	- mfc\lib\eafxisd.pdb
	  (Before) Size:   372,736  Date: 06/18/96  Time: 06:45p
	  (After)          380,928        09/12/96        01:54a
	
	- mfc\src\except.cpp
	  (Before) Size:     8,733  Date: 05/14/96  Time: 11:34p
	  (After)            8,733        09/12/96        01:07a
	
	- mfc\src\filefind.cpp
	  (Before) Size:     7,698  Date: 06/03/96  Time: 02:01p
	  (After)            7,692        09/12/96        01:07a
	
	- mfc\src\filemem.cpp
	  (Before) Size:     8,155  Date: 10/09/95  Time: 01:29p
	  (After)            8,224        09/12/96        01:07a
	
	- mfc\src\inet.cpp
	  (Before) Size:    61,254  Date: 06/13/96  Time: 07:01p
	  (After)           67,004        09/12/96        01:07a
	
	- mfc\src\inetimpl.cpp
	  (Before) Size:    13,539  Date: 06/12/96  Time: 03:17p
	  (After)           14,149        09/12/96        01:07a
	
	- mfc\src\inetimpl.h
	  (Before) Size:    10,160  Date: 06/12/96  Time: 03:17p
	  (After)           10,693        09/12/96        01:07a
	
	- mfc\src\isapi.cpp
	  (Before) Size:    48,559  Date: 06/03/96  Time: 02:01p
	  (After)           48,608        09/12/96        01:07a
	
	- mfc\src\map_so.cpp
	  (Before) Size:     8,865  Date: 10/09/95  Time: 01:29p
	  (After)            8,936        09/12/96        01:08a
	
	- mfc\src\map_sp.cpp
	  (Before) Size:     8,092  Date: 10/09/95  Time: 01:27p
	  (After)            8,163        09/12/96        01:08a
	
	- mfc\src\map_ss.cpp
	  (Before) Size:     9,111  Date: 10/09/95  Time: 01:29p
	  (After)            9,127        09/12/96        01:08a
	
	- mfc\src\intel\mfc42.def
	  (Before) Size:   375,779  Date: 06/19/96  Time: 10:03a
	  (After)          376,857        09/12/96        02:26a
	
	- mfc\lib\MFC42.LIB
	  (Before) Size: 4,163,666  Date: 06/19/96  Time: 10:03a
	  (After)        4,174,336        09/12/96        02:26a
	
	- mfc\src\intel\mfc42d.def
	  (Before) Size:   253,445  Date: 06/19/96  Time: 10:01a
	  (After)          254,054        09/25/96        05:36p
	
	- mfc\lib\MFC42D.LIB
	  (Before) Size: 2,980,212  Date: 06/19/96  Time: 10:01a
	  (After)        2,986,310        09/25/96        05:36p
	
	- mfc\src\intel\mfc42u.def
	  (Before) Size:   375,543  Date: 06/19/96  Time: 10:06a
	  (After)          376,613        09/25/96        05:40p
	
	- mfc\lib\MFC42U.LIB
	  (Before) Size: 4,167,310  Date: 06/19/96  Time: 10:06a
	  (After)        4,177,948        09/25/96        05:41p
	
	- mfc\src\intel\mfc42ud.def
	  (Before) Size:   253,953  Date: 06/19/96  Time: 10:04a
	  (After)          254,488        09/25/96        05:39p
	
	- mfc\lib\MFC42UD.LIB
	  (Before) Size: 2,991,054  Date: 06/19/96  Time: 10:04a
	  (After)        2,996,056        09/25/96        05:39p
	
	- bin\ide\mfcapwz.dll
	  (Before) Size:  922,384  Date: 06/20/96  Time: 11:24p Version: 4.20.6166
	  (After)         925,968        08/29/96        03:07p          4.20.6201
	
	- bin\mfcclswz.dll
	  (Before) Size:  645,904  Date: 06/20/96  Time: 11:25p Version: 4.20.6167
	  (After)         650,512        08/29/96        03:03p          4.20.6242
	
	- mfc\src\intel\mfcd42d.def
	  (Before) Size:    42,252  Date: 06/19/96  Time: 10:02a
	  (After)           42,307        09/12/96        02:16a
	
	- mfc\lib\MFCD42D.LIB
	  (Before) Size:   484,232  Date: 06/19/96  Time: 10:02a
	  (After)          484,232        09/12/96        02:16a
	
	- mfc\src\intel\mfcd42ud.def
	  (Before) Size:    42,188  Date: 06/19/96  Time: 10:05a
	  (After)           42,243        09/12/96        02:35a
	
	- mfc\lib\MFCD42UD.LIB
	  (Before) Size:   483,898  Date: 06/19/96  Time: 10:05a
	  (After)          483,898        09/12/96        02:35a
	
	- mfc\src\intel\mfcn42d.def
	  (Before) Size:     7,798  Date: 06/19/96  Time: 10:02a
	  (After)            7,853        09/12/96        02:16a
	
	- mfc\lib\MFCN42D.LIB
	  (Before) Size:    91,134  Date: 06/19/96  Time: 10:02a
	  (After)           91,134        09/12/96        02:16a
	
	- mfc\src\intel\mfcn42ud.def
	  (Before) Size:     7,767  Date: 06/19/96  Time: 10:05a
	  (After)            7,822        09/12/96        02:36a
	
	- mfc\lib\mfcn42ud.lib
	  (Before) Size:    90,740  Date: 06/19/96  Time: 10:05a
	  (After)           90,740        09/12/96        02:36a
	
	- mfc\src\intel\mfco42d.def
	  (Before) Size:   199,812  Date: 06/19/96  Time: 10:02a
	  (After)          201,359        09/12/96        02:15a
	
	- mfc\lib\mfco42d.lib
	  (Before) Size: 2,144,026  Date: 06/19/96  Time: 10:02a
	  (After)        2,156,938        09/12/96        02:15a
	
	- mfc\src\intel\mfco42ud.def
	  (Before) Size:   199,704  Date: 06/19/96  Time: 10:05a
	  (After)          201,431        09/12/96        02:34a
	
	- mfc\lib\mfco42ud.lib
	  (Before) Size: 2,146,982  Date: 06/19/96  Time: 10:05a
	  (After)        2,159,362        09/12/96        02:34a
	
	- mfc\src\mfcole.mak
	  (Before) Size:     4,682  Date: 06/13/96  Time: 07:01p
	  (After)            4,683        09/12/96        01:08a
	
	- mfc\lib\mfcs42.lib
	  (Before) Size:   147,418  Date: 06/18/96  Time: 07:18p
	  (After)          147,454        09/12/96        02:26a
	
	- mfc\lib\mfcs42.pdb
	  (Before) Size:   708,608  Date: 06/18/96  Time: 07:18p
	  (After)          700,416        09/12/96        02:26a
	
	- mfc\lib\mfcs42d.lib
	  (Before) Size:   149,516  Date: 06/18/96  Time: 07:03p
	  (After)          149,552        09/12/96        02:11a
	
	- mfc\lib\mfcs42d.pdb
	  (Before) Size:   716,800  Date: 06/18/96  Time: 07:03p
	  (After)          716,800        09/12/96        02:11a
	
	- mfc\lib\mfcs42u.lib
	  (Before) Size:   147,590  Date: 06/18/96  Time: 07:38p
	  (After)          147,624        09/12/96        02:45a
	
	- mfc\lib\mfcs42u.pdb
	  (Before) Size:   708,608  Date: 06/18/96  Time: 07:38p
	  (After)          700,416        09/12/96        02:45a
	
	- mfc\lib\mfcs42ud.lib
	  (Before) Size:   149,906  Date: 06/18/96  Time: 07:23p
	  (After)          149,940        09/12/96        02:31a
	
	- mfc\lib\mfcs42ud.pdb
	  (Before) Size:   716,800  Date: 06/18/96  Time: 07:23p
	  (After)          716,800        09/12/96        02:31a
	
	- mfc\lib\nafxcw.lib
	  (Before) Size: 7,543,504  Date: 06/18/96  Time: 06:44p
	  (After)        7,586,968        09/12/96        01:53a
	
	- mfc\lib\nafxcw.pdb
	  (Before) Size:   733,184  Date: 06/18/96  Time: 06:44p
	  (After)          741,376        09/12/96        01:53a
	
	- mfc\lib\nafxcwd.lib
	  (Before) Size: 8,440,612  Date: 06/18/96  Time: 06:36p
	  (After)        8,501,750        09/12/96        01:46a
	
	- mfc\lib\nafxcwd.pdb
	  (Before) Size:   749,568  Date: 06/18/96  Time: 06:36p
	  (After)          749,568        09/12/96        01:46a
	
	- mfc\lib\nafxis.lib
	  (Before) Size:   100,204  Date: 06/18/96  Time: 06:45p
	  (After)           88,028        09/12/96        01:54a
	
	- mfc\lib\nafxisd.lib
	  (Before) Size:    97,438  Date: 06/18/96  Time: 06:44p
	  (After)           97,840        09/12/96        01:53a
	
	- mfc\lib\nafxisd.pdb
	  (Before) Size:    69,632  Date: 06/18/96  Time: 06:44p
	  (After)           69,632        09/12/96        01:53a
	
	- mfc\src\occcont.cpp
	  (Before) Size:    17,689  Date: 06/13/96  Time: 07:01p
	  (After)           17,693        09/12/96        01:08a
	
	- mfc\src\oleasmon.cpp
	  (Before) Size:    12,861  Date: 06/13/96  Time: 07:01p
	  (After)           16,759        09/12/96        01:08a
	
	- mfc\src\olebind.h
	  (Before) Size:     2,813  Date: 06/03/96  Time: 02:03p
	  (After)            2,811        09/12/96        01:08a
	
	- mfc\src\oleconn.cpp
	  (Before) Size:    12,981  Date: 06/03/96  Time: 02:01p
	  (After)           12,981        09/12/96        01:08a
	
	- mfc\src\oledocob.cpp
	  (Before) Size:    24,624  Date: 06/07/96  Time: 04:08p
	  (After)           25,016        09/12/96        01:08a
	
	- mfc\src\oledoctg.cpp
	  (Before) Size:     5,486  Date: 06/13/96  Time: 07:02p
	  (After)            5,937        09/12/96        01:08a
	
	- mfc\src\oledocvw.cpp
	  (Before) Size:    11,826  Date: 06/07/96  Time: 04:05p
	  (After)           11,851        09/12/96        01:08a
	
	- mfc\src\olefact.cpp
	  (Before) Size:    14,097  Date: 06/11/96  Time: 03:06p
	  (After)           14,008        09/12/96        01:08a
	
	- mfc\src\oleimpl.h
	  (Before) Size:    31,186  Date: 06/03/96  Time: 05:22p
	  (After)           31,105        09/12/96        01:08a
	
	- mfc\src\oleimpl2.h
	  (Before) Size:    10,381  Date: 06/03/96  Time: 02:03p
	  (After)           10,477        09/12/96        01:08a
	
	- mfc\src\oleinit.cpp
	  (Before) Size:     6,874  Date: 06/03/96  Time: 02:02p
	  (After)            6,954        09/12/96        01:08a
	
	- mfc\src\oleipfrm.cpp
	  (Before) Size:    19,762  Date: 05/10/96  Time: 01:59p
	  (After)           19,741        09/12/96        01:08a
	
	- mfc\src\olemisc.cpp
	  (Before) Size:    39,592  Date: 06/03/96  Time: 02:02p
	  (After)           39,685        09/12/96        01:08a
	
	- mfc\src\olemon.cpp
	  (Before) Size:     8,758  Date: 06/12/96  Time: 03:49p
	  (After)            8,858        09/12/96        01:08a
	
	- mfc\src\olepro32.cpp
	  (Before) Size:     3,995  Date: 05/31/96  Time: 11:58a
	  (After)            4,021        09/12/96        01:08a
	
	- mfc\src\olestrm.cpp
	  (Before) Size:    11,557  Date: 05/14/96  Time: 02:25p
	  (After)           11,865        09/12/96        01:08a
	
	- mfc\src\olesvr1.cpp
	  (Before) Size:    77,615  Date: 06/12/96  Time: 03:17p
	  (After)           77,667        09/12/96        01:08a
	
	- mfc\src\ppgpict.cpp
	  (Before) Size:    11,333  Date: 05/28/96  Time: 10:41a
	  (After)           11,341        09/12/96        01:08a
	
	- mfc\src\sockcore.cpp
	  (Before) Size:    31,842  Date: 06/05/96  Time: 10:27a
	  (After)           31,826        09/12/96        01:08a
	
	- mfc\src\thrdcore.cpp
	  (Before) Size:    24,872  Date: 06/03/96  Time: 02:02p
	  (After)           24,972        09/12/96        01:08a
	
	- mfc\lib\uafxcw.lib
	  (Before) Size: 7,577,428  Date: 06/18/96  Time: 06:59p
	  (After)        7,617,746        09/12/96        02:07a
	
	- mfc\lib\uafxcw.pdb
	  (Before) Size:   741,376  Date: 06/18/96  Time: 06:58p
	  (After)          741,376        09/12/96        02:07a
	
	- mfc\lib\uafxcwd.lib
	  (Before) Size: 8,475,500  Date: 06/18/96  Time: 06:51p
	  (After)        8,536,952        09/12/96        02:00a
	
	- mfc\lib\uafxcwd.pdb
	  (Before) Size:   749,568  Date: 06/18/96  Time: 06:51p
	  (After)          749,568        09/12/96        02:00a
	
	- mfc\src\viewcore.cpp
	  (Before) Size:    14,682  Date: 06/03/96  Time: 02:02p
	  (After)           14,821        09/12/96        01:08a
	
	- mfc\src\viewprev.cpp
	  (Before) Size:    32,817  Date: 10/09/95  Time: 01:29p
	  (After)           32,961        09/12/96        01:08a
	
	- mfc\src\viewrich.cpp
	  (Before) Size:    57,619  Date: 06/10/96  Time: 05:21p
	  (After)           58,063        09/12/96        01:08a
	
	- mfc\src\wincore.cpp
	  (Before) Size:   102,800  Date: 06/03/96  Time: 02:02p
	  (After)          102,814        09/12/96        01:08a
	
	This is the end of Part 2.
	
	REFERENCES
	==========
	
	You can find the (http://support.microsoft.com/download/support/mslfiles/the)
	additional parts of this article on the Microsoft Knowledge Base:
	
	  Q160491 INFO: Files Modified by VC42b Patch - Part 1 of 4
	
	  Q160505 INFO: Files Modified by VC42b Patch - Part 3 of 4
	
	  Q160506 INFO: Files Modified by VC42b Patch - Part 4 of 4
	
	Additional query words: patch
	
	======================================================================
	Keywords          : kbenv kbother kbnokeyword kbDAOsearch kbDatabase kbGenInfo kbMFC kbODBC kbVC kbHWx86 kbArtTypeINF 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC32bitSearch
	Version           : 4.2
	
	=============================================================================
	

{% endraw %}
