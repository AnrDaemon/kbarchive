---
layout: page
title: "Q142211: BUG: Blob Persistent Data Incorrect for Ported OLE Control"
permalink: /kb/142/Q142211/
---

## Q142211: BUG: Blob Persistent Data Incorrect for Ported OLE Control

{% raw %}

	Article: Q142211
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbole kbCtrl kbMFC kbVBX kbVC400bug kbVC410bug kbGrpDSMFCATLkbbuglist
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ 32-bit Edition, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An OLE control using PX_Blob(), created using the Control Developer's Kit (CDK)
	that shipped with Visual C++ 2.2 or earlier and saved in a Visual Basic 4.0
	form, may give undefined behavior if the control is ported to Visual C++ 4.0 or
	4.1 and the Visual Basic form containing the control is reopened. To read in the
	blob data correctly, you must force the container to use an interface other than
	IPropertyBag to serialize the data. In this case, a 20-byte header will not be
	expected and the blob data should be read in properly. The technique
	demonstrated in the "Sample Code" section of this article unexposes the
	control's IPersistPropertyBag interface thereby forcing the container to use an
	interface other than IPropertyBag to read in the blob data.
	
	CAUSE
	=====
	
	OLE Controls created using the CDK that shipped with Visual C++ 2.2 or earlier
	did not implement the IPersistPropertyBag interface. Controls created with
	Visual C++ 4.0 or 4.1 do implement IPersistPropertyBag.
	
	The undefined behavior is due to Visual Basic's implementation of IPropertyBag.
	Visual Basic is currently adding a 20-byte header to a blob property's
	persistent data, and expecting that header to be in any blob persistent data
	previously saved. In the case of controls created previously to Visual C++ 4.0
	or 4.1, IPersistPropertyBag, which corresponds to the container's IPropertyBag
	was not implemented. Therefore, the container used a different means to
	serialize the blob data which did not attach a 20 byte header. The undefined
	behavior may behave a number of ways including the blob data being
	reinitialized, blob data being initialized incorrectly, or the control not being
	created altogether.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in Microsoft Visual Basic 4.0.
	
	MORE INFORMATION
	================
	
	Sample Code to Demonstrate Workaround
	-------------------------------------
	
	The following is a step by step process to unexpose the IPersistPropertyBag
	interface in an OLE control generated with Visual C++ 4.0 or 4.1. This is most
	easily done by implementing a new interface map, which does not expose the
	IPersistPropertyBag interface.
	
	1. In the declaration of your COleControl derived class (in the header file),
	  add a DECLARE_INTERFACE_MAP() macro if there isn't one already there.
	
	     class CBlobTestCtrl : public COleControl
	     {
	     ...
	         DECLARE_INTERFACE_MAP()
	     };
	
	2. In the .cpp file for the control, implement a new interface map specifying
	  all but IID_IPersistPropertyBag.
	
	     BEGIN_INTERFACE_MAP(CBlobTestCtrl, CWnd)  // use CWnd not COleControl
	         INTERFACE_PART(CBlobTestCtrl, IID_IOleObject, OleObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_IConnectionPointContainer,
	           ConnPtContainer)
	         INTERFACE_PART(CBlobTestCtrl, IID_IOleControl, OleControl)
	         INTERFACE_PART(CBlobTestCtrl, IID_IPersist, PersistStorage)
	         INTERFACE_PART(CBlobTestCtrl, IID_IPersistMemory, PersistMemory)
	         INTERFACE_PART(CBlobTestCtrl, IID_IPersistStreamInit,
	           PersistStreamInit)
	         INTERFACE_PART(CBlobTestCtrl, IID_IOleInPlaceObject,
	           OleInPlaceObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_IOleInPlaceActiveObject,
	           OleInPlaceActiveObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_IDispatch, Dispatch)
	         INTERFACE_PART(CBlobTestCtrl, IID_IOleCache, OleCache)
	         INTERFACE_PART(CBlobTestCtrl, IID_IViewObject, ViewObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_IViewObject2, ViewObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_IDataObject, DataObject)
	         INTERFACE_PART(CBlobTestCtrl, IID_ISpecifyPropertyPages,
	           SpecifyPropertyPages)
	         INTERFACE_PART(CBlobTestCtrl, IID_IPerPropertyBrowsing,
	           PerPropertyBrowsing)
	         INTERFACE_PART(CBlobTestCtrl, IID_IProvideClassInfo,
	           ProvideClassInfo)
	         INTERFACE_PART(CBlobTestCtrl, IID_IProvideClassInfo2,
	           ProvideClassInfo)
	         INTERFACE_PART(CBlobTestCtrl, IID_IPersistStorage, PersistStorage)
	     END_INTERFACE_MAP()
	
	REFERENCES
	==========
	
	MFC Technical Note #38 about "MFC/OLE IUnknown implementation" Inside Ole Second
	Edition by Kraig Brockschmidt
	
	Additional query words: 4.00 4.10
	
	======================================================================
	Keywords          : kbole kbCtrl kbMFC kbVBX kbVC400bug kbVC410bug kbGrpDSMFCATL kbbuglist
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
