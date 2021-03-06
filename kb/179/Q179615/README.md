---
layout: page
title: "Q179615: HOWTO: Specify or Change a Remote Server's Location at Run Time"
permalink: /kb/179/Q179615/
---

## Q179615: HOWTO: Specify or Change a Remote Server's Location at Run Time

{% raw %}

	Article: Q179615
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbDCOM kbVBp kbVBp500 kbVBp600 kbGrpDSVBDB kbDSupport
	Last Modified: 12-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0, used with:
	   - the operating system: Microsoft Windows NT 
	   - the operating system: Microsoft Windows 2000 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0, used with:
	   - the operating system: Microsoft Windows NT 
	   - the operating system: Microsoft Windows 2000 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0, used with:
	   - the operating system: Microsoft Windows NT 
	   - the operating system: Microsoft Windows 2000 
	-------------------------------------------------------------------------------
	
	IMPORTANT NOTE: This article was written as a solution for Visual Basic 5.0, when the CreateObject function did not have the second optional parameter, which allows it to select the remote server computer. PLEASE NOTE: You should not use the solution that is described in this article if you are using Visual Basic version 6.0 or later. To accomplish the same results, you can simply provide the second parameter in the CreateObject function.
	
	If you decide to use the solution that is described in this article, please be aware that the solution implies to make changes in the registry. Therefore, the solution only works if the user that is running the application has Administrator rights on operating systems such as Windows NT or Windows 2000.
	
	SUMMARY
	=======
	
	This article demonstrates how to programmatically change a remote DCOM server's
	actual computer location. This change enables a remote client to be directed to
	any computer that has the server component installed without the need to restart
	the client or register the new server object. This is accomplished by using the
	WIN32 API to make modifications to the registry. The sample below provides two
	functions that wrap the needed API calls cleanly: SetRemoteServer and
	GetRemoteServer.
	
	NOTE: Late binding must be used to accomplish this behavior at run-time.
	
	MORE INFORMATION
	================
	
	Add the following constants, declarations, and the two public functions to a
	standard module in your project:
	
	        'API Function and Constant Declarations
	
	        Public Const REG_NONE = 0             'No value type
	        Public Const REG_SZ = 1               'Unicode null terminated string
	        Public Const REG_EXPAND_SZ = 2        'Unicode null terminated string
	        Public Const REG_BINARY = 3              'Free form binary
	        Public Const REG_DWORD = 4               '32-bit number
	        Public Const REG_DWORD_LITTLE_ENDIAN = 4 '(same as REG_DWORD)
	        Public Const REG_DWORD_BIG_ENDIAN = 5    '32-bit number
	        Public Const REG_LINK = 6                'Symbolic Link (unicode)
	        Public Const REG_MULTI_SZ = 7            'Multiple Unicode strings
	
	        Public Const HKEY_CLASSES_ROOT = &H80000000
	        Public Const HKEY_CURRENT_USER = &H80000001
	        Public Const HKEY_LOCAL_MACHINE = &H80000002
	        Public Const HKEY_USERS = &H80000003
	        Public Const HKEY_CURRENT_CONFIG = &H80000005
	
	        Public Const ERROR_SUCCESS = 0
	        Public Const ERROR_NONE = 0
	        Public Const ERROR_BADDB = 1
	        Public Const ERROR_BADKEY = 2
	        Public Const ERROR_CANTOPEN = 3
	        Public Const ERROR_CANTREAD = 4
	        Public Const ERROR_CANTWRITE = 5
	        Public Const ERROR_OUTOFMEMORY = 6
	        Public Const ERROR_INVALID_PARAMETER = 7
	        Public Const ERROR_ACCESS_DENIED = 8
	        Public Const ERROR_INVALID_PARAMETERS = 87
	        Public Const ERROR_NO_MORE_ITEMS = 259
	        Public Const KEY_ALL_ACCESS = &H3F
	        Public Const REG_OPTION_NON_VOLATILE = 0
	
	     Private Declare Function RegCloseKey Lib "advapi32.dll" _
	        (ByVal hKey As Long) As Long
	     Private Declare Function RegOpenKey Lib "advapi32.dll" _
	         Alias "RegOpenKeyA" (ByVal hKey As Long, _
	         ByVal lpSubKey As String, _
	         phkResult As Long) As Long
	     Private Declare Function RegOpenKeyEx Lib "advapi32.dll"  _
	         Alias "RegOpenKeyExA" _
	        (ByVal hKey As Long, _
	         ByVal lpSubKey As String, _
	         ByVal ulOptions As Long, _
	         ByVal samDesired As Long, _
	         phkResult As Long) As Long
	     Private Declare Function RegQueryValue Lib "advapi32.dll" _
	         Alias "RegQueryValueA" _
	        (ByVal hKey As Long, _
	         ByVal lpSubKey As String, _
	         ByVal lpValue As String, _
	         lpcbValue As Long) As Long
	     Private Declare Function RegQueryValueEx Lib "advapi32.dll"  _
	         Alias "RegQueryValueExA" _
	        (ByVal hKey As Long, _
	         ByVal lpValueName As String, _
	         ByVal lpReserved As Long, _
	         lpType As Long, _
	         lpData As Any, _
	         lpcbData As Long) As Long
	     Private Declare Function RegSetValue Lib "advapi32.dll" _
	         Alias "RegSetValueA" _
	        (ByVal hKey As Long, _
	         ByVal lpSubKey As String, _
	         ByVal dwType As Long, _
	         ByVal lpData As String, _
	         ByVal cbData As Long) As Long
	     Private Declare Function RegSetValueEx Lib "advapi32.dll" _
	         Alias "RegSetValueExA" _
	        (ByVal hKey As Long, _
	         ByVal lpValueName As String, _
	         ByVal Reserved As Long, _
	         ByVal dwType As Long, _
	         lpData As Any, _
	         ByVal cbData As Long) As Long
	
	        'GetRemoteServer function
	        Public Function GetRemoteServer(ClassName As String) As String
	
	        Dim lRetVal As Long      'result of the API functions
	        Dim hKey As Long         'handle of opened key
	        Dim sKeyName As String
	        Dim lpType As Long
	        Dim lpData As String
	        Dim lpcbData As Long
	        Dim myclsid As String
	        Dim MyServerName As String
	
	         sKeyName = ClassName
	         If sKeyName = "" Then
	          MsgBox "This is not a valid class name"
	          GetRemoteServer = "None"
	          Exit Function
	         End If
	         lRetVal = RegOpenKey(HKEY_CLASSES_ROOT, sKeyName, hKey)
	         If lRetVal = ERROR_SUCCESS Then
	          lpcbData = 40
	          lpData = Space$(40)
	          lRetVal = RegQueryValue(hKey, "CLSID", lpData, lpcbData)
	          If lRetVal = ERROR_NONE Then
	           myclsid = Left$(lpData, lpcbData - 1)
	           RegCloseKey (hKey)
	           sKeyName = "AppID\" & myclsid
	           lRetVal = RegOpenKeyEx(HKEY_CLASSES_ROOT, sKeyName, 0, _
	                KEY_ALL_ACCESS, hKey)
	           If lRetVal = ERROR_SUCCESS Then
	            lpcbData = 255
	            lpData = Space$(255)
	            lRetVal = RegQueryValueEx(ByVal hKey, "RemoteServerName", 0, _
	                 ByVal lpType, ByVal lpData, lpcbData)
	            If lRetVal = ERROR_NONE Then
	             MyServerName = Left$(lpData, lpcbData - 1)
	             GetRemoteServer = MyServerName
	            Else
	             MsgBox lRetVal & " - This class is not registered remotely."
	             GetRemoteServer = "None"
	            End If
	           Else
	            MsgBox lRetVal & " - Cannot find CLSID for " & sKeyName
	            GetRemoteServer = "None"
	           End If
	           RegCloseKey (hKey)
	          End If
	         Else
	          MsgBox lRetVal & " - Cannot find class name - " & sKeyName
	          GetRemoteServer = "None"
	         End If
	
	         Exit Function
	        QueryValueExExit:
	         MsgBox lRetVal
	         GetRemoteServer = "None"
	         Exit Function
	        QueryValueExError:
	         Resume QueryValueExExit
	        End Function
	
	        'SetRemoteServer function
	      Public Function SetRemoteServer(ClassName As String, _
	            NewRemote As String) As String
	
	        Dim lRetVal As Long      'result of the API functions
	        Dim hKey As Long         'handle of opened key
	        Dim sKeyName As String
	        Dim lpType As Long
	        Dim lpData As String
	        Dim lpcbData As Long
	        Dim myclsid As String
	        Dim MyServerName As String
	
	        If NewRemote <> "" Then
	         MyServerName = NewRemote
	         sKeyName = ClassName
	         If sKeyName = "" Then
	          MsgBox "You did not enter a class name"
	          SetRemoteServer = "None"
	          Exit Function
	         End If
	         lRetVal = RegOpenKey(HKEY_CLASSES_ROOT, sKeyName, hKey)
	         If lRetVal = ERROR_SUCCESS Then
	          lpcbData = 40
	          lpData = Space$(40)
	          lRetVal = RegQueryValue(hKey, "CLSID", lpData, lpcbData)
	          If lRetVal = ERROR_NONE Then
	           myclsid = Left$(lpData, lpcbData - 1)
	           RegCloseKey (hKey)
	           sKeyName = "AppID\" & myclsid
	           lRetVal = RegOpenKeyEx(HKEY_CLASSES_ROOT, sKeyName, 0&, _
	                KEY_ALL_ACCESS, hKey)
	           If lRetVal = ERROR_SUCCESS Then
	            lpcbData = Len(MyServerName) + 1
	            lpData = MyServerName
	            lpType = REG_SZ
	            lRetVal = RegSetValueEx(hKey, "RemoteServerName", 0&, lpType, _
	                 ByVal lpData, lpcbData)
	             If lRetVal = ERROR_NONE Then
	              SetRemoteServer = MyServerName
	             Else
	              MsgBox lRetVal & " - This class is not registered remotely."
	              SetRemoteServer = "None"
	             End If
	            Else
	             MsgBox lRetVal & " - Cannot find CLSID for " & sKeyName
	             SetRemoteServer = "None"
	            End If
	            RegCloseKey (hKey)
	           End If
	          Else
	           MsgBox lRetVal & " - Cannot find class name - " & sKeyName
	           SetRemoteServer = "None"
	          End If
	         Else
	          MsgBox "Invalid Parameter - NewRemote"
	          SetRemoteServer = "None"
	         End If
	         Exit Function
	        QueryValueExExit:
	         MsgBox lRetVal
	         SetRemoteServer = "None"
	         Exit Function
	        QueryValueExError:
	         Resume QueryValueExExit
	        End Function
	
	You can now call these functions from anywhere in your project.
	
	NOTE: The server object must be declared using late binding:
	
	     Private MyServer as Object
	     Set MyServer = CreateObject("YourServer.YourClass")
	
	GetRemoteServer Function
	------------------------
	
	You can call this function at any time to retrieve the current remote computer
	name that a remotely-registered class is set up to use. Pass the
	object.classname to the function, and its return value will be either the
	RemoteMachineName or "None" if there was an error. For example:
	
	     Dim ClassName as String
	     Dim MachineName as String
	
	     ClassName = "YourServer.YourClass"      'The name of your object
	     MachineName = GetRemoteServer(ClassName)
	     If MachineName = "None" Then
	      MsgBox "Error retrieving machine name"
	     Else
	      MsgBox "The machine name is " & MachineName
	     End If
	
	SetRemoteServer Function
	------------------------
	
	NOTE: It is recommended that you set any current references to this object to
	"Nothing" before changing the server location via this function.
	
	To change the remote computer on which your server will run, pass the
	object.classname and the new remote computer name to this method. The return
	value will be either the New remote computer name or "None" if there was an
	error. The next CreateObject that is called for this object will then use the
	new server location. For example:
	
	     dim MyServer as Object
	     dim ClassName as String
	     dim MachineName as String
	     dim NewMachine as String
	
	     Set MyServer = Nothing                  'Clear existing reference
	     ClassName = "YourServer.YourClass"      'The name of your object
	     NewMachine = "MachineToChangeTo"        'The name of the new machine
	     MachineName = SetRemoteServer(ClassName, NewMachine)
	     If MachineName = NewMachine Then
	      Set MyServer = CreateObject(ClassName) 'connect to the new machine
	     Else
	      MsgBox "Error Setting machine name"
	     End If
	
	NOTE: The Remote ActiveX Server applications must be set up and functioning
	correctly for the code above to work properly.
	
	Additional query words: DCOM RemoteServerName DCOMCNFG OLEView
	
	======================================================================
	Keywords          : kbDCOM kbVBp kbVBp500 kbVBp600 kbGrpDSVBDB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2
	Version           : :5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
