---
layout: page
title: "Q190225: HOWTO: Do a MergeCells with FlexGrid or Hierarchical FlexGrid"
permalink: /kb/190/Q190225/
---

## Q190225: HOWTO: Do a MergeCells with FlexGrid or Hierarchical FlexGrid

{% raw %}

	Article: Q190225
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp500 kbVBp600 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The MergeCells property determines whether cells with the same contents should
	be grouped in a single cell spanning multiple rows or columns. The different
	values available for MergeCells let you specify how the cell merging should be
	handled. Setting MergeCells to a value other than zero enables cell merging. To
	have the FlexGrid or Hierarchical FlexGrid perform the merge, you must set the
	MergeCol or MergeRow property to True for each Column or Row you want to merge.
	
	MORE INFORMATION
	================
	
	This example uses the FlexGrid control. You can substitute the Hierarchical
	FlexGrid for the FlexGrid control in this sample.
	
	When MergeRow or MergeColumn are True, the merged row or column may not merge
	correctly with a fixed column or row. The sample project in this article
	demonstrates this problem. Merging works best with non-fixed columns and rows.
	
	This sample demonstrates merging with MergeCells set to FlexMergeFree. This
	allows merging on any row or column that has the MergeRow or MergeCol property
	set to True.
	
	Steps to Create Sample Project
	------------------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Click Components on the Projects menu to open the Components dialog box. On
	  the Controls tab, select Microsoft FlexGrid Control and click OK.
	
	3. Place a FlexGrid control and four CommandButtons on Form1.
	
	4. Add the following code to code window for Form1:
	
	        Option Explicit
	        Dim iFixedRows As Integer
	        Dim iFixedCols As Integer
	
	        Private Sub Command1_Click()
	          iFixedCols = iFixedCols + 1
	          If iFixedCols > MSFlexGrid1.Cols - 1 Then
	            iFixedCols = MSFlexGrid1.Cols - 1
	            MsgBox "No more columns to fix"
	          Else
	            MSFlexGrid1.FixedCols = iFixedCols
	          End If
	        End Sub
	
	        Private Sub Command2_Click()
	          iFixedCols = iFixedCols - 1
	          If iFixedCols < 0 Then
	            iFixedCols = 0
	            MsgBox "No more Columns to unfix"
	          Else
	            MSFlexGrid1.FixedCols = iFixedCols
	          End If
	        End Sub
	
	        Private Sub Command3_Click()
	          iFixedRows = iFixedRows + 1
	          If iFixedRows > MSFlexGrid1.Rows - 1 Then
	            iFixedRows = MSFlexGrid1.Rows - 1
	            MsgBox "No more rows to fix"
	          Else
	            MSFlexGrid1.FixedRows = iFixedRows
	          End If
	        End Sub
	
	        Private Sub Command4_Click()
	          iFixedRows = iFixedRows - 1
	          If iFixedRows< 0 Then
	            iFixedRows = 0
	            MsgBox "No more rows to unfix"
	          Else
	            MSFlexGrid1.FixedRows = iFixedRows
	          End If
	        End Sub
	
	        Private Sub Form_Load()
	          Command1.Caption = "Increment fixed Columns"
	          Command2.Caption = "Decrease fixed Columns"
	          Command3.Caption = "Increment fixed Rows"
	          Command4.Caption = "Decrease fixed Rows"
	
	          FillFlexGrid 'call sub that puts data into grid
	
	          iFixedRows = MSFlexGrid1.FixedRows
	          iFixedCols = MSFlexGrid1.FixedCols
	        End Sub
	
	        Private Sub FillFlexGrid()
	          Dim sEntry As String
	          With MSFlexGrid1
	            .Cols = 5 'set the number of columns
	            ' Set FixedRows to 0 so you can use AddItem. You can't
	            ' use AddItem with a FixedRow. You have to use the Text property
	            .FixedRows = 0
	            .MergeCells = flexMergeFree 'Set the MergeCells property.
	            .Font.Name = "fixedsys"
	            .Font.Size = 8
	            .Row = 0
	            .Col = 0
	            .ColWidth(0) = 1750
	
	            ' Add some data to the grid using AddItem.
	            sEntry = "Region" & vbTab & "Region" & vbTab & "Employee"
	            .AddItem sEntry, 0
	            sEntry = "Northwest" & vbTab & "Bats" & vbTab & "Bats"
	            .AddItem sEntry, 1
	            sEntry = "Northwest" & vbTab & "Whahoos"
	            .AddItem sEntry, 2
	            sEntry = "Northwest" & vbTab & "Whahoos"
	            .AddItem sEntry, 3
	            sEntry = "Northwest" & vbTab & "Sharks"
	            .AddItem sEntry, 4
	            sEntry = "Southeast" & vbTab & "Panthers"
	            .AddItem sEntry, 5
	            sEntry = "Southeast" & vbTab & "Panthers"
	            .AddItem sEntry, 6
	            sEntry = "Southeast" & vbTab & "Desktops"
	            .AddItem sEntry, 7
	            sEntry = "Southeast" & vbTab & "Desktops"
	            .AddItem sEntry, 8
	            sEntry = "Mid-Atlantic" & vbTab & "VSx7"
	            .AddItem sEntry, 9
	            sEntry = "Mid-Atlantic" & vbTab & "VSx7"
	            .AddItem sEntry, 10
	
	            ' Set the rows and columns you want to merge.
	            .MergeCol(0) = True 'First Column in grid
	            .MergeCol(1) = True 'Second Column in grid
	
	            .MergeRow(0) = True 'First Row in Grid
	            .MergeRow(1) = True 'Second Row in Grid
	            ' Set the fixed columns and rows.
	            .FixedCols = 1
	            .FixedRows = 1
	          End With
	        End Sub
	
	5. Save and run the project. Use the CommandButtons to add or remove fixed
	  columns or rows to see how they affect a merged column or row.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Brian Combs, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp500 kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
