# PQ Snippets

### Quick Snippets
* [Text.From](https://docs.microsoft.com/en-us/powerquery-m/text-from)([Year]) & "W" & [Text.PadStart](https://docs.microsoft.com/en-us/powerquery-m/text-padstart)(Text.From([Week of Year]),2,"0")
*  Underscore _ references to the current row (record) of the table. e.g., #"Removed Columns" = Table.RemoveColumns(#"Changed Type", List.Select(Table.ColumnNames(#"Changed Type"), each Text.EndsWith(_,"Price"))) // remove all columns that end with "Price"
* Add Leading Zeros; Text.End( "000" & Text.From ([MonthNo] ), 4 ), Text.PadStart( Text.From( [MonthNo] ), 4, "0" )
* Get named range value: Excel.CurrentWorkbook(){[Name=NamedRange]}[Content]{0}[Column1]
* Last Refreshed Date: DateTime.LocalNow()

## Custom Functions

-----
### ConvertRuntimeToMinutes
* To use the function in Power Query, simply add a custom column and apply the function to your runtime column, like this: ConvertRuntimeToMinutes([Runtime]), where ConvertRuntimeToMinutes is the name of the function and [Runtime] is your column name. Examples "2h 22m" => 142, "1h 45m" => 105, "3h" => 180, "45m" => 45.
```
(source as text) as number =>
let
    isEmpty = source = null or source = "",
    result = if isEmpty then 0 else
        let
            hasHours = Text.Contains(source, "h"),
            hasMinutes = Text.Contains(source, "m"),
            hours = if hasHours then Number.FromText(Text.BeforeDelimiter(source, "h")) else 0,
            minutes = if hasMinutes then 
                if hasHours then Number.FromText(Text.BeforeDelimiter(Text.AfterDelimiter(source, "h"), "m")) 
                else Number.FromText(Text.BeforeDelimiter(source, "m"))
                else 0,
            totalMinutes = hours * 60 + minutes
        in
            totalMinutes
in
    result

```

-----

### TypeChecker
* This custom function in Power Query, named TypeChecker, determines the data type of a given column, identifying it as "Text", "Number", "Date", or "Other", and also handles null values by returning "Null".

```
let
    // Define the custom function with a parameter
    TypeChecker = (inputColumn as any) as text =>
    let
        // Check if the input is null
        result = if inputColumn = null then "Null"

                 // If not null, determine the data type
                 else
                 let
                     dataType = Value.Type(inputColumn),
                     typeResult = if dataType = type text then "Text"
                                  else if dataType = type number then "Number"
                                  else if dataType = type datetime or dataType = type date then "Date"
                                  else "Other"
                 in
                     typeResult
    in
        result
in
    TypeChecker


```

#### FilteredQuery
```
= Table.SelectRows(Source, each ([DateTypeCheck] <> "Date" 
or [TextTypeCheck] <> "Text"
or [NumberGreaterThanCheck] = true
))
```

#### Trim Special Edges
```
// Removes leading and trailing characters from the specified list.

= Text.Trim("__- Hello World -,", {",", "-", " ", "_"})
```


#### Remove Last Character

```
 =
    Table.TransformColumns(
        #"Previous Step",
        {
            {"Number of Ratings - Copy",
             each Number.FromText(Text.Start(_, Text.Length(_) - 1)),
             type number}
        }
    )
```
