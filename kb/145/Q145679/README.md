---
layout: page
title: "Q145679: HOWTO: Use the Registry API to Save and Retrieve Setting"
permalink: /kb/145/Q145679/
---

## Q145679: HOWTO: Use the Registry API to Save and Retrieve Setting

{% raw %}

	Article: Q145679
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbnokeyword kbtophit KbVBA kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbDSuppo
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic for Applications versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Although Visual Basic includes the SaveSetting and GetSetting functions to save
	and retrieve information from the registry, these functions only operate on a
	specific section of the registry, the Visual Basic and VBA Program Settings of
	the HKEY_CURRENT_USER root key.
	
	This article outlines the use of 32-bit Windows API functions, which can be used
	to set and retrieve values from anywhere in the registry. The topics and
	function references in this article can be generalized to program the 16-bit
	registry.
	
	The 32-bit API functions also include support for security, although an overview
	of security is outside the scope of this article.
	
	NOTE: The SaveSetting and GetSetting functions are not part of the VBA function
	library. However, the sample code below still applies to 32-bit applications
	that implement VBA.
	
	MORE INFORMATION
	================
	
	General Registry Information
	----------------------------
	
	The registry is used by applications and Windows to store configuration data. It
	is a replacement for the large numbers of INI files that proliferated on Windows
	3.x machines and is also used heavily by OLE.
	
	The registry is organized using a hierarchical series of keys and values
	resembling a tree. Each key, beginning with one of the six predefined root keys,
	can have sub-keys and values associated with it. The keys are organizational and
	naming units and appear in the Windows Registry Editors as file folders. Values
	are data entries and appear as text entries in the right pane of the Registry
	Editor window. Keys need not have any associated values, but may have many. Each
	value has an associated data type. The two most commonly used registry data
	types are REG_SZ, a null-terminated string; and REG_DWORD, a 32-bit number.
	
	The basic process used to write or read from a location in the registry is the
	same. To reference any given key or value, you must have a handle to the key.
	Once this handle is obtained, values and sub-keys of the key that this handle
	refers to can be read, set, or listed (enumerated).
	
	Given a location in the registry, to obtain a handle to that key, you must begin
	with one of the six predefined keys (HKEY_CLASSES_ROOT, HKEY_CURRENT_USER,
	HKEY_LOCAL_MACHINE, HKEY_USERS, HKEY_CURRENT_CONFIG, and HKEY_DYN_DATA) and
	traverse the registry tree until the desired key is reached. User programs most
	often read and write from HKEY_CURRENT_USER and HKEY_LOCAL_MACHINE. If the keys
	being traversed exist already, you can use a series of calls to the RegOpenKey
	or RegOpenKeyEx functions. If the keys need to be created, the RegCreateKey and
	RegCreateKeyEx functions do the job.
	
	With the handle to the desired key, the functions used to list, set, and retrieve
	information can be called. In all cases, the functions with the Ex suffix will
	work only on 32-bit platforms. Functions without the suffix may work on both
	16-bit and 32-bit versions of Windows. Keep in mind that not all registry
	functions lacking the 'Ex' suffix are functions provided for 16-bit
	compatibility. The Ex suffix was only added when the capabilities of 16-bit
	functions were expanded. Functions that are totally new and specific to 32-bit
	platforms do not possess an Ex extension.
	
	The RegSetValue and RegSetValueEx functions allow the settings of a value to be
	modified, while RegQueryValue and RegQueryValueEx retrieve the current setting
	of a value. The limitations of the non-Ex, 16-bit versions of these APIs are
	very evident here. When using the 16-bit RegSetValue function there is no way to
	name a value, and because of this, RegSetValue can't be used to associate more
	than one value with each key. In addition, all values written with RegSetValue
	have a data type of REG_SZ. These limitations are inherent with the 16-bit
	Registry. RegSetValueEx allows the creation of a multiple number of values with
	any available data type.
	
	How to Write to a Specific Registry Location
	--------------------------------------------
	
	After determining what functions you will need to use for your project, copy the
	relevant declares from the code at the end of this article to a basic module.
	The two Visual Basic procedures included (SetValueEx and QueryValueEx) are
	wrappers for the RegSetValueEx and RegQueryValueEx API functions and greatly
	simplify their use. The notes below make use of these Visual Basic functions;
	however, you are free to make calls directly to the API if you wish.
	
	Creating/Modifying Keys and Values:
	
	With the declarations and procedures available, you can create and open keys, and
	add, modify, and read values. The three following sections explain how to create
	a key, set or modify a value, and query a value.
	
	Creating a New Key:
	
	Creating a new key is as simple as using the following procedure. CreateNewKey
	takes the name of the key to create, and the constant representing the
	predefined key to create the key under. The call to RegCreateKeyEx doesn't take
	advantage of the security mechanisms allowed, but could be modified to do so. A
	discussion of Registry security is outside the scope of this article.
	
	     Private Sub CreateNewKey (sNewKeyName As String, lPredefinedKey As Long)
	         Dim hNewKey As Long         'handle to the new key
	         Dim lRetVal As Long         'result of the RegCreateKeyEx function
	
	         lRetVal = RegCreateKeyEx(lPredefinedKey, sNewKeyName, 0&, _
	                   vbNullString, REG_OPTION_NON_VOLATILE, KEY_ALL_ACCESS, _
	                   0&, hNewKey, lRetVal)
	         RegCloseKey (hNewKey)
	     End Sub
	
	With this procedure a call of:
	
	     CreateNewKey "TestKey", HKEY_LOCAL_MACHINE
	
	will create a key called TestKey immediately under HKEY_LOCAL_MACHINE.
	
	Calling CreateNewKey like this:
	
	        CreateNewKey "TestKey\SubKey1\SubKey2", HKEY_LOCAL_MACHINE
	
	will create three-nested keys beginning with TestKey immediately under
	HKEY_CURRENT_USER, SubKey1 subordinate to TestKey, and SubKey3 under SubKey2.
	
	Setting/Modifying a Value:
	
	Creating and setting a value of a specified key can be accomplished with the
	following short procedure. SetKeyValue takes the key that the value will be
	associated with, the name of the value, the setting of the value, and the type
	of the value (the SetValueEx function only supports REG_SZ and REG_DWORD, but
	this can be modified if necessary). Specifying a new value for an existing
	sValueName will modify the current setting of that value.
	
	     Private Sub SetKeyValue (sKeyName As String, sValueName As String, _
	     vValueSetting As Variant, lValueType As Long)
	         Dim lRetVal As Long         'result of the SetValueEx function
	         Dim hKey As Long         'handle of open key
	
	         'open the specified key
	         lRetVal = RegOpenKeyEx(HKEY_CURRENT_USER, sKeyName, 0, _
	                                   KEY_SET_VALUE, hKey)
	         lRetVal = SetValueEx(hKey, sValueName, lValueType, vValueSetting)
	         RegCloseKey (hKey)
	     End Sub
	
	A call of:
	
	     SetKeyValue "TestKey\SubKey1", "StringValue", "Hello", REG_SZ
	
	will create a value of type REG_SZ called "StringValue" with the setting of
	"Hello." This value will be associated with the key SubKey1 of "TestKey."
	
	In this case, "TestKey" is a subkey of HKEY_CURRENT_USER, but this can be
	modified by changing the call to RegOpenKeyEx. This call will fail if
	"TestKey\SubKey1" does not exist. To avoid this problem, use a call to
	RegCreateKeyEx instead of a call to RegOpenKeyEx. RegCreateKeyEx will open a
	specified key if it already exists.
	
	Querying a Value:
	
	The next procedure can be used to ascertain the setting of an existing value.
	QueryValue takes the name of the key and the name of a value associated with
	that key and displays a message box with the corresponding value. It uses a call
	to the QueryValueEx wrapper function defined below, that only supports REG_SZ
	and REG_DWORD types.
	
	     Private Sub QueryValue (sKeyName As String, sValueName As String)
	         Dim lRetVal As Long         'result of the API functions
	         Dim hKey As Long         'handle of opened key
	         Dim vValue As Variant      'setting of queried value
	
	         lRetVal = RegOpenKeyEx(HKEY_CURRENT_USER, sKeyName, 0, _
	     KEY_QUERY_VALUE, hKey)
	         lRetVal = QueryValueEx(hKey, sValueName, vValue)
	         MsgBox vValue
	         RegCloseKey (hKey)
	     End Sub
	
	With this procedure, a call of:
	
	     QueryValue "TestKey\SubKey1", "StringValue"
	
	will display a message box with the current setting of the "StringValue" value,
	and assumes that "StringValue" exists in the "TestKey\SubKey1" key.
	
	If the Value that you query does not exist then QueryValue will return an error
	code of 2 - 'ERROR_BADKEY'.
	
	Additional Notes:
	
	The above examples use the extended 32-bit versions of the registry functions
	exclusively. These functions allow more than one value to be associated with
	each key. As discussed above, the 16-bit RegSetValue and RegQueryValue act on a
	single value associated with the current key (which is always of the type
	REG_SZ). These functions appear in the 32-bit Registry Editor with a name of
	<NO NAME>. To set, modify, or query this special associated value, one
	must use the 16-bit registry functions. Reading and writing from the registry in
	a 16-bit environment is much simpler than in a 32-bit environment. The same
	basic procedure is followed: open a key and get a handle and then call your
	modification function with that handle, but no consideration needs to be made
	for multiple associated values or for different value data types. A 16-bit
	application can create and modify keys and values with the declarations of the
	RegCreateKey, RegOpenKey, RegQueryValue, RegSetValue, and RegCloseKey
	functions.
	
	In some cases, there is no need for any values to be associated with a key. An
	application may only need to know if a certain key or value exists, and not care
	about the nature of the key's values. In a situation like this, the RegEnumKey,
	RegEnumKeyEx, and RegEnumValue functions can be used to determine whether a
	certain key or value exists. For more information on these functions refer to
	the API Text Viewer and/or Windows API reference.
	
	API Function and Constant Declarations
	--------------------------------------
	
	     Option Explicit
	
	     Public Const REG_SZ As Long = 1
	     Public Const REG_DWORD As Long = 4
	
	     Public Const HKEY_CLASSES_ROOT = &H80000000
	     Public Const HKEY_CURRENT_USER = &H80000001
	     Public Const HKEY_LOCAL_MACHINE = &H80000002
	     Public Const HKEY_USERS = &H80000003
	
	     Public Const ERROR_NONE = 0
	     Public Const ERROR_BADDB = 1
	     Public Const ERROR_BADKEY = 2
	     Public Const ERROR_CANTOPEN = 3
	     Public Const ERROR_CANTREAD = 4
	     Public Const ERROR_CANTWRITE = 5
	     Public Const ERROR_OUTOFMEMORY = 6
	     Public Const ERROR_ARENA_TRASHED = 7
	     Public Const ERROR_ACCESS_DENIED = 8
	     Public Const ERROR_INVALID_PARAMETERS = 87
	     Public Const ERROR_NO_MORE_ITEMS = 259
	
	     Public Const KEY_QUERY_VALUE = &H1
	     Public Const KEY_SET_VALUE = &H2
	     Public Const KEY_ALL_ACCESS = &H3F
	
	     Public Const REG_OPTION_NON_VOLATILE = 0
	
	     Declare Function RegCloseKey Lib "advapi32.dll" _
	     (ByVal hKey As Long) As Long
	     Declare Function RegCreateKeyEx Lib "advapi32.dll" Alias _
	     "RegCreateKeyExA" (ByVal hKey As Long, ByVal lpSubKey As String, _
	     ByVal Reserved As Long, ByVal lpClass As String, ByVal dwOptions _
	     As Long, ByVal samDesired As Long, ByVal lpSecurityAttributes _
	     As Long, phkResult As Long, lpdwDisposition As Long) As Long
	     Declare Function RegOpenKeyEx Lib "advapi32.dll" Alias _
	     "RegOpenKeyExA" (ByVal hKey As Long, ByVal lpSubKey As String, _
	     ByVal ulOptions As Long, ByVal samDesired As Long, phkResult As _
	     Long) As Long
	     Declare Function RegQueryValueExString Lib "advapi32.dll" Alias _
	     "RegQueryValueExA" (ByVal hKey As Long, ByVal lpValueName As _
	     String, ByVal lpReserved As Long, lpType As Long, ByVal lpData _
	     As String, lpcbData As Long) As Long
	     Declare Function RegQueryValueExLong Lib "advapi32.dll" Alias _
	     "RegQueryValueExA" (ByVal hKey As Long, ByVal lpValueName As _
	     String, ByVal lpReserved As Long, lpType As Long, lpData As _
	     Long, lpcbData As Long) As Long
	     Declare Function RegQueryValueExNULL Lib "advapi32.dll" Alias _
	     "RegQueryValueExA" (ByVal hKey As Long, ByVal lpValueName As _
	     String, ByVal lpReserved As Long, lpType As Long, ByVal lpData _
	     As Long, lpcbData As Long) As Long
	     Declare Function RegSetValueExString Lib "advapi32.dll" Alias _
	     "RegSetValueExA" (ByVal hKey As Long, ByVal lpValueName As String, _
	     ByVal Reserved As Long, ByVal dwType As Long, ByVal lpValue As _
	     String, ByVal cbData As Long) As Long
	     Declare Function RegSetValueExLong Lib "advapi32.dll" Alias _
	     "RegSetValueExA" (ByVal hKey As Long, ByVal lpValueName As String, _
	     ByVal Reserved As Long, ByVal dwType As Long, lpValue As Long, _
	     ByVal cbData As Long) As Long
	
	SetValueEx and QueryValueEx Wrapper Functions:
	
	     Public Function SetValueEx(ByVal hKey As Long, sValueName As String, _
	     lType As Long, vValue As Variant) As Long
	         Dim lValue As Long
	         Dim sValue As String
	         Select Case lType
	             Case REG_SZ
	                 sValue = vValue & Chr$(0)
	                 SetValueEx = RegSetValueExString(hKey, sValueName, 0&, _
	                                                lType, sValue, Len(sValue))
	             Case REG_DWORD
	                 lValue = vValue
	                 SetValueEx = RegSetValueExLong(hKey, sValueName, 0&, _
	     lType, lValue, 4)
	             End Select
	     End Function
	
	     Function QueryValueEx(ByVal lhKey As Long, ByVal szValueName As _
	     String, vValue As Variant) As Long
	         Dim cch As Long
	         Dim lrc As Long
	         Dim lType As Long
	         Dim lValue As Long
	         Dim sValue As String
	
	         On Error GoTo QueryValueExError
	
	         ' Determine the size and type of data to be read
	         lrc = RegQueryValueExNULL(lhKey, szValueName, 0&, lType, 0&, cch)
	         If lrc <> ERROR_NONE Then Error 5
	
	         Select Case lType
	             ' For strings
	             Case REG_SZ:
	                 sValue = String(cch, 0)
	
	     lrc = RegQueryValueExString(lhKey, szValueName, 0&, lType, _
	     sValue, cch)
	                 If lrc = ERROR_NONE Then
	                     vValue = Left$(sValue, cch-1)
	                 Else
	                     vValue = Empty
	                 End If
	             ' For DWORDS
	             Case REG_DWORD:
	     lrc = RegQueryValueExLong(lhKey, szValueName, 0&, lType, _
	     lValue, cch)
	                 If lrc = ERROR_NONE Then vValue = lValue
	             Case Else
	                 'all other data types not supported
	                 lrc = -1
	         End Select
	
	     QueryValueExExit:
	         QueryValueEx = lrc
	         Exit Function
	
	     QueryValueExError:
	         Resume QueryValueExExit
	     End Function
	
	REFERENCES
	==========
	
	Programming the Windows 95 User Interface, Chapter 10 - "Using the Registry"
	
	For function references: Any guide to the Win16 or Win32 API.
	
	Additional query words: registry
	
	======================================================================
	Keywords          : kbcode kbnokeyword kbtophit KbVBA kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbDSupport kbVB500 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVBASearch kbZNotKeyword3 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
