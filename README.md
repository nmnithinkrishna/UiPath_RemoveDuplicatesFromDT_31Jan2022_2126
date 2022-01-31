# UiPath_RemoveDuplicatesFromDT_31Jan2022_2126

UiPath - Removing duplicates from datatable &amp; arranging with latest data

https://forum.uipath.com/t/is-there-a-way-to-delineate-columns-for-removing-duplicates-in-excel-using-uipath/395639/2

**Core Logic**

```
dt_Input.AsEnumerable.Select(Function(row) _
	dt_Temp.Rows.Add(row.ItemArray.Concat(
		New Object() { String.Concat(row("First Name").ToString.Trim, row("Last Name").ToString.Trim, row("Facility").ToString.Trim, row("Claim Number").ToString.Trim) }
	).ToArray)
).GroupBy(Function(row) row("Comparer").ToString).Select(Function(grp) dt_Temp.Rows.Add(grp.OrderBy(Function(obj) obj("TimeStamp").ToString).Last().ItemArray)).CopyToDataTable
```
