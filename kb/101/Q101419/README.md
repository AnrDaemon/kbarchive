---
layout: page
title: "Q101419: The DCB Structure in Windows 3.1"
permalink: /kb/101/Q101419/
---

## Q101419: The DCB Structure in Windows 3.1

{% raw %}

	Article: Q101419
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The data control block (DCB) structure defines the control setting for a serial
	communications device. OpenComm() and BuildCommDCB() both initialize a DCB
	structure. However, there are many fields in the DCB that cannot be changed
	using these procedures. These fields can be updated directly, and these changes
	can be applied to the communications port using SetCommState().
	
	MORE INFORMATION
	================
	
	OpenComm() uses BuildCommDCB() with "COM1:9600, E, 7, 1" as the lpszDef
	parameter to build a default DCB. OpenComm() internally calls SetCommState()
	with this default DCB to set the initial state of the communications port.
	
	BuildCommDCB() can be used to initialize a DCB with certain settings. This
	procedure takes a string in the same format as the MS-DOS mode command for its
	lpszDef parameter. For example, BuildCommDCB("COM1:9600, n, 8, 1", &myDCB)
	sets myDCB to have a baud rate of 9600, no parity, 8-bit byte size, and 1 stop
	bit. This string needs to contain only the COM port and baud rate; if the other
	values are absent, they will default. The default settings are even parity, byte
	size of 7, and 1 stop bit. SetCommState() must be called to put the new DCB
	settings into effect.
	
	SetCommState() takes a DCB as a parameter, and sets the port according to all the
	parameters. A DCB can be initialized by calling BuildCommDCB() or the current
	settings can be returned by calling GetCommState(). In addition, the fields in
	the DCB can be modified directly. After a DCB is changed, SetCommState() must be
	used to apply the setting to the port.
	
	Below is a summary of all the DCB fields. Each field has a description of what
	happens in BuildCommDCB(). The information that follows SetCommState() indicates
	how the DCB can be manipulated manually. That DCB can then be used in the lpDCB
	parameter to SetCommState().
	
	Id - The ID of the port. This is set by BuildCommDCB(), and is the
	    same as the OpenComm() return value.
	
	BaudRate - BuildCommDCB() - The baud rate is based on the first two
	    characters in the baud rate position in the MS-DOS mode string. For
	    example, "COM1:96,n,8,1" will set the baud rate to 9600. The only
	    baud rates that can be set are 110, 150, 300, 600,1200, 2400,
	    4800, 9600, and 19200. If none of these baud rates are used,
	    BuildCommDCB() returns an error.
	
	    SetCommState() - The BaudRate field can set any baud rate up to 57,600
	    by either setting the BaudRate field in the DCB to one of the
	    CBR_baudrate constants, or to any number greater than 2 and less
	    than CBR_110. Numbers outside this range result in SetCommState()
	    returning an IE_BAUDRATE error.
	
	ByteSize - BuildCommDCB() - Specifying any number other than 7 or 8
	    results in an error.
	
	    SetCommState() - The byteSize field can be set to any number between
	    4 and 8. Numbers outside this range result in SetCommState()
	    returning an IE_BYTESIZE error.
	
	Parity - BuildCommDCB - The parity can be set to "E" (even), "O"
	    (odd), "N" (none), "M" (mark) or "S" (space).
	
	    SetCommState() - The Parity field in the DCB can be set to NOPARITY,
	    ODDPARITY, EVENPARITY, MARKPARITY, or SPACEPARITY. Other settings
	    result in SetCommState() returning and IE_DEFAULT error.
	
	StopBits - BuildCommDCB - Stop bits of 1 or 2 are accepted. Any other
	    value (including 1.5) returns an error.
	
	    SetCommDCB() - The StopBits field can be set to ONESTOPBIT,
	    ONE5STOPBITS, or TWOSTOPBITS. Other settings result in
	    SetCommState() returning an IE_DEFAULT error.
	
	The time-out field, RlsTimeout, CtsTimeout, or DsrTimeout, enables time-out
	checking if its value is anything other than zero. This time-out checking occurs
	during WriteComm() regardless of any other values in the DCB, including
	fOutxCtsFlow and fOutxDsrFlow. Specifying INFINITE does not really enable
	infinite time-out. The value is set to -1 (which is 65536), which makes the
	time-out approximately 65 seconds. If a time-out occurs, WriteComm() returns 0
	(zero), and GetCommError() returns a time-out error (CE_CTSTO, CE_DSRTO, or
	CE_RLSDTO).
	
	RlsTimeout - BuildCommDCB() - If the 6th parameter of the MS-DOS mode
	    string is specified as P, then this time-out is infinite (set to
	    -1). Any other value returns an error. If it is not specified, it
	    defaults to (zero).
	
	    SetCommDCB() - RlsTimeout can be set to IGNORE, INFINITE, or any
	    number.
	
	    This field is the amount of time, in milliseconds, to wait for
	    RLSD (same as Carrier Detect) to become high, before copying any
	    data to the transmit queue during WriteComm().
	
	CtsTimeout - BuildCommDCB() - MS-DOS mode string translated exactly like
	    RlsTimeout.
	
	   SetCommDCB() - CtsTimeout can be set to IGNORE, INFINITE, or any
	   number.
	
	   This field is the amount of time, in milliseconds, to wait for
	   CTS (Clear to Send) to become high before copying any data to the
	   transmit queue during WriteComm().
	
	DsrTimeout - BuildCommDCB() - MS-DOS mode string translated exactly like
	   RlsTimeout.
	
	   SetCommDCB() - DsrTimeout can be set to IGNORE, INFINITE, or any
	   number.
	
	   This field is the amount of time, in milliseconds, to wait for DSR
	   (Data Set Ready) to become high before copying any data to the
	   transmit queue during WriteComm().
	
	   All of the following flags are set to 0 in BuildCommDCB(), except
	   for fBinary, which is set to 1. Any of these can be set to 0 or 1
	   before calling SetCommState().
	
	   fBinary - If fBinary is set to zero, reception of the EofChar
	       character indicates the end of the input stream. ReadComm()
	       will not return any characters past EofChar. If any characters
	       are received after EofChar, it will be treated as overflowing
	       the receive queue (CE_RXOVER). The reception of EofChar is
	       indicated in the COMSTAT status flag CSTF_EOF. If fBinary is
	       set to one, the EofChar character has no special meaning.
	
	   fRtsDisable - RTS flow control is used ONLY if fRtsDisable is set
	       to 0, and fRtsFlow is set to one. Any other combination will
	       disable RTS flow control.
	
	       OpenComm() will set RTS high, and it will remain high unless
	       RTS flow control is enabled or fRtsDisable is set.
	
	          fRtsDisable        fRtsFlow         RTS state
	          ---------------------------------------------
	
	             0               0                 Set High
	             0               1           RTS flow control enabled
	             1               0                 Set low
	             1               1                 Set low
	
	       CloseComm() does not change the state of RTS or DTR,
	       regardless of the state of the disable settings, but it drops
	       them momentarily while closing the port.
	
	       If RTS or DTR are not being used for flow control, they can be
	       manipulated using EscapeCommFuntion().
	
	   fDtrDisable - Used with fDtrFlow. Functions similar to
	       fRtsDisable/fRtsFlow.
	
	   fRtsflow - See fRtsDisable.
	
	   fDtrflow - See fDtrDisable and fRtsDisable.
	
	   fParity - Specifies whether parity checking is enabled. If this
	       flag is set, parity checking is performed, and CE_RXPARITY
	       errors are reported.
	
	       ReadComm() will return a negative value if it encounters an
	       error (such as a parity error). GetCommError()is used to
	       retrieve and clear that error. To receive notification of a
	       parity error, SetCommEventMask() can be used to enable EV_ERR
	       events. GetCommEventMask() should be used to clear the event,
	       however, GetCommError() must still be used to clear the error.
	
	   fOutxCtsFlow - Specifies that CTS signal is to be monitored for
	       output flow control. If this flag is set and CTS is turned
	       off, output is suspended until CTS is again set.
	
	       If the CtsTimeout field contains any value other than zero,
	       WriteComm() will wait for CTS, regardless of the value of
	       fOutxCtsFlow.
	
	   fOutxDsrFlow - Specifies that DSR signal is to be monitored for
	       output flow control. If this flag is set and DSR is turned
	       off, output is suspended until DSR is again set.
	
	       If the DsrTimeout field contains any value other than zero,
	       WriteComm() will wait for DSR, regardless of the value of
	       fOutxDsrFlow.
	
	   fDummy - Reserved.
	
	   fOutX - Specifies that X-on/X-off flow control is used during
	       transmission. If this flag is set, transmission stops when the
	       XoffChar is received and starts again when the XonChar is
	       received.
	
	       If transmission is waiting as a result of the X-off character
	       being received, the CSTF_XOFFHOLD flag in the COMSTAT
	       structure will be set.
	
	   fInX - Specifies that X-on/X-off flow control is used during
	       reception. If this flag is set, the XoffChar character is sent
	       when the reception queue comes within XoffLim characters of
	       being full and the XonChar character is sent when the
	       reception queue comes within XonLim characters of being empty.
	
	       If transmission is waiting as a result of the X-off character
	       being transmitted, the CSTF_XOFFSENT flag is set in the
	       COMSTAT structure.
	
	   fPeChar - Specifies that characters received with parity errors
	       are to be replaced with the character specified by PeChar.
	
	   fNull - Specifies that received null character are to be
	       discarded.
	
	   fChEvt - Not actually used.
	
	   fDummy2 - Reserved.
	
	XonChar - BuildCommDCB() - Set to 0x11 (CTRL+Q) SetCommState() - Can
	   be set to any character.
	
	   This field is the X-on character for both transmit and receive.
	   See fInX and fOutX.
	
	XoffChar - BuildCommDCB() - Set to 0x13 (CTRL+S) SetCommState() - Can
	   be set to any character.
	
	   This field is the X-off character for both transmit and receive.
	   See fInX and fOutX.
	
	XonLim - BuildCommSCB() - Set to 10. SetCommState() - Can be set to
	   any value.
	
	   When the number of characters in the receive queue drops below
	   this value, the X-on character is sent, if enabled, and DTR is
	   set, if enabled. See fInX and fOutX.
	
	XoffLim - BuildCommDCB() - Set to 10. SetCommState() - can be set to
	   any value.
	
	   When the number of characters in the receive queue exceeds this
	   value, the X-off character is sent, if enabled, and DTR is
	   dropped, if enabled. See fInX and fOutX.
	
	PeChar - BuildCommDCB() - Set to 0. SetCommState() - Can be set to any
	   character.
	
	   Parity error replacement character. See fPeChar and fParity.
	
	EofChar - BuildCommDCB() - Set to 0. SetCommState() - Can be set to
	   any character.
	
	   Character which specifies end of input. See fBinary.
	
	EvtChar - BuildCommDCB() - Set to 0. SetCommState() - Can be set to
	   any character.
	
	   Specifies the value of the character to be used to signal an
	   event. When this value is received, an EV_RXFLAG event will be
	   generated. The fChEvt flag is not actually used. Use
	   SetCommEventMask() to enable these events.
	
	TxDelay - Not actually used.
	
	Additional query words: 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
