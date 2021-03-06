---
layout: page
title: "Q158612: STL Sample for the vector::(empty, erase, push_back) Functions"
permalink: /kb/158/Q158612/
---

## Q158612: STL Sample for the vector::(empty, erase, push_back) Functions

{% raw %}

	Article: Q158612
	Product(s): Microsoft C Compiler
	Version(s): 4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbVC420 kbVC500 kbVC600 kbDSupport
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Standard C++ Library, used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following sample code illustrates how to use two vector::erase functions,
	the vector::empty function, and the vector::push_back STL functions in Visual
	C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     <vector>
	
	Prototypes
	----------
	
	     template<class _TYPE, class _A>
	     void vector::push_back(const _TYPE& X);
	
	     template<class _TYPE, class _A>
	     iterator vector::erase(iterator Iterator);
	
	     template<class _TYPE, class _A>
	     iterator vector::erase(iterator First, iterator Last);
	
	     template<class _TYPE, class _A>
	     bool vector::empty() const;
	
	NOTE: The class/parameter names in the prototype may not match the version in the
	header file. Some have been modified to improve readability.
	
	Description
	-----------
	
	The sample declares an empty vector of integers. It adds 10 integers to the
	vector, then displays the contents of the vector. It deletes the sixth element
	by using erase, and then displays the contents of the vector again. It deletes
	the rest of the elements using a different form of erase, then displays the
	vector (now empty) again. The ShowVector routine uses the empty function to
	determine whether to generate the contents of the vector.
	
	Sample Code
	-----------
	
	NOTE: The first line in the sample code is:
	
	  // Compile options needed: /GX
	
	In VC++ .NET, /EHsc is set by default and is equivalent to /GX.
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: /GX
	  // 
	  //    Empty.cpp -- Illustrates the vector::empty and vector::erase
	  //                 functions.
	  //                 Also demonstrates the vector::push_back function.
	  // 
	  // Functions:
	  // 
	  //    vector::empty - Returns true if vector has no elements.
	  // 
	  //    vector::erase - Deletes elements from a vector (single & range).
	  // 
	  //    vector::begin - Returns an iterator to start traversal of the
	  //                    vector.
	  // 
	  //    vector::end - Returns an iterator for the last element of the
	  //                  vector.
	  // 
	  //    vector::push_back - Appends (inserts) an element to the end of a
	  //                        vector, allocating memory for it if necessary.
	  // 
	  //    vector::iterator - Traverses the vector.
	  // 
	  // Written by Tom Campbell
	  // of Microsoft Corporation
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  // The debugger can't handle symbols more than 255 characters long.
	  // STL often creates symbols longer than that.
	  // When symbols are longer than 255 characters, the warning is disabled.
	  #pragma warning(disable:4786)
	
	  #include <iostream>
	  #include <vector>
	
	  #if _MSC_VER > 1020   // if VC++ version is > 4.2
	     using namespace std;  // std c++ libs implemented in std
	     #endif
	
	  typedef vector<int, allocator<int> > INTVECTOR;
	
	  const ARRAY_SIZE = 10;
	
	  void ShowVector(INTVECTOR &theVector);
	
	  void main()
	  {
	      // Dynamically allocated vector begins with 0 elements.
	      INTVECTOR theVector;
	
	      // Intialize the vector to contain the numbers 0-9.
	      for (int cEachItem = 0; cEachItem < ARRAY_SIZE; cEachItem++)
	          theVector.push_back(cEachItem);
	
	      // Output the contents of the dynamic vector of integers.
	      ShowVector(theVector);
	
	      // Using void iterator erase(iterator Iterator) to
	      // delete the 6th element (Index starts with 0).
	      theVector.erase(theVector.begin() + 5);
	
	      // Output the contents of the dynamic vector of integers.
	      ShowVector(theVector);
	
	      // Using iterator erase(iterator First, iterator Last) to
	      // delete a range of elements all at once.
	      theVector.erase(theVector.begin(), theVector.end());
	
	      // Show what's left (actually, nothing).
	      ShowVector(theVector);
	  }
	
	  // Output the contents of the dynamic vector or display a
	  // message if the vector is empty.
	  void ShowVector(INTVECTOR &theVector)
	  {
	      // First see if there's anything in the vector. Quit if so.
	      if (theVector.empty())
	      {
	          cout << endl << "theVector is empty." << endl;
	          return;
	      }
	
	      // Iterator is used to loop through the vector.
	      INTVECTOR::iterator theIterator;
	
	      // Output contents of theVector.
	      cout << endl << "theVector [ " ;
	      for (theIterator = theVector.begin(); theIterator != theVector.end();
	           theIterator++)
	      {
	          cout << *theIterator;
	          if (theIterator != theVector.end()-1) cout << ", ";
	                                                // cosmetics for the output
	      }
	      cout << " ]" << endl ;
	  }
	
	Program Output
	--------------
	
	theVector [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
	
	theVector [ 0, 1, 2, 3, 4, 6, 7, 8, 9 ]
	
	theVector is empty.
	
	REFERENCES
	==========
	
	Visual C++ Books Online: Visual C++ Books; C/C++; Standard C++ Library Reference
	
	Additional query words: STL STLSample
	
	======================================================================
	Keywords          : kbcode kbVC420 kbVC500 kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVCLibrary
	Version           : :4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
