# PQ Snippets

* [Text.From](https://docs.microsoft.com/en-us/powerquery-m/text-from)([Year]) & "W" & [Text.PadStart](https://docs.microsoft.com/en-us/powerquery-m/text-padstart)(Text.From([Week of Year]),2,"0")

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
