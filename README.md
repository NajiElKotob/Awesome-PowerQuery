# Awesome PowerQuery
{Awesome Works in Progress}

`
Microsoft’s Data Connectivity and Data Preparation technology that lets you seamlessly access data stored in hundreds of sources and reshape it to fit your needs—all with an easy to use, engaging, no-code experience.` [learn more](https://powerquery.microsoft.com/)

`
Where the 'M'agic happens!
`

## YouTube :tv:
* [Curbal - Power Query](https://www.youtube.com/watch?v=dbTvOk1IyNU&list=PLDz00l_jz6zxF_OSmQhWBCVmQOaROoxWj)
* [Pragmatic Works](https://www.youtube.com/user/PragmaticWorks/search?query=Power+Query)
* [Power Query Jumpstarter](https://www.youtube.com/watch?v=7Vn6uOxcAc0&list=PLHYaVuyjhcqyYD7qss7lsFVBLf8B_zZrx) - Brian Grant

## Videos
* [Power BI Dev Camp March Intro to M Programming](https://www.youtube.com/watch?v=BsgOU9eeCBg)



-----

## Learning
* [Power Query - Microsoft Learn](https://learn.microsoft.com/en-us/training/browse/?products=power-query&source=learn)


## Blogs
### Power Query
* [Chris Webb's BI Blog](https://blog.crossjoin.co.uk/) - Chris Webb
* [Power Query](https://www.powerquery.io/) - powerquery.io
### Power Query Online
* [Visual Data Prep](https://powerbi.microsoft.com/en-us/blog/announcing-visual-data-prep-general-availability-diagram-view-in-power-query-online/)

-----

## Connectors
* [PowerQuery Connectors (GitHub)](https://github.com/MicrosoftDocs/powerquery-docs/tree/main/powerquery-docs/Connectors)

-----
## M Language
* [Power Query M formula language](https://docs.microsoft.com/en-us/powerquery-m/)
* [Quick tour of the Power Query M formula language](https://docs.microsoft.com/en-us/powerquery-m/quick-tour-of-the-power-query-m-formula-language)

* [IF Statements](https://www.myonlinetraininghub.com/power-query-if-statements) - myonlinetraininghub.com

-----

## Tools and Add-ins
* [Power Query Formatter](https://powerqueryformatter.com/) - Beautify your Power Query (M-Language) Code with Power Query Formatter 
* [Power Query SDK](https://marketplace.visualstudio.com/items?itemName=Dakahn.PowerQuerySDK) - A Power Query language service for Visual Studio
* [Power Query Source (SSIS)](https://docs.microsoft.com/en-us/sql/integration-services/data-flow/power-query-source)

-----
## Articles

* [Value from previous row, using List.Range](https://exceltown.com/en/tutorials/power-bi/powerbi-com-and-power-bi-desktop/power-bi-data-sources/power-query-get-value-from-previous-row/) - exceltown.com

### General
* [Power Query Skills Apply to Excel, Power BI and SSAS Tabular](https://sqlserverbi.blog/2017/12/04/power-query-skills-apply-to-excel-power-bi-and-ssas-tabular/)
* [Comparing ‘null’ values in Power Query](http://excel-inside.pro/blog/2018/05/17/comparing-null-values-in-power-query/)
* [Power Query tips for every Power BI Developer](https://towardsdatascience.com/power-query-tips-for-every-power-bi-developer-da9ebd3dcd93) - Nikola Ilic

## Transformation
### Organizing
* Folders
* Comments
* Rename
### Combine Data
* [Append queries](https://docs.microsoft.com/en-us/power-query/append-queries) - The append operation creates a single table by adding the contents of one or more tables to another.
### Splitting
* Delimeters with more than one character e.g., ;;
### Consolidation
* Grouping
* Aggregating
* Merging
* Extract data from file name
### Columns
* [Using M to dynamically change column names in PowerQuery](https://exceed.hr/blog/using-m-to-dynamically-change-column-names-in-powerquery/) - Krešimir Ledinski (October 2020)
* Ghost columns e.g., Empty columns in excel
### Errors and Diagnostics
* [4 Ways to Fix Date Errors in Power Query + Locale & Regional Settings](https://www.excelcampus.com/powerquery/power-query-date-errors-settings/) - Jon Acampora (April 2020)
* [Awesome Way To Log in Power Query M Using Diagnostics.Trace](https://blog.learningtree.com/awesome-way-log-power-query-m-using-diagnostics-trace/) - Dan Buskirk (June 2016)
* [Viewing Error Messages For All Rows In Power Query](https://blog.crossjoin.co.uk/2014/12/22/viewing-error-messages-for-all-rows-in-power-query/) - Chris Webb (December 2014)

### Dates and Times
* Deal with differnt date regions
### JSON
* [How to Parse Custom JSON Data using Excel](https://theexcelclub.com/how-to-parse-custom-json-data-using-excel/)

### Remove Duplicates
* [Keep The Most Recent Entry](https://www.excelguru.ca/blog/2016/05/25/keep-the-most-recent-entry/) - Ken Puls (May 2016)
* [Remove Duplicate Doesn’t Work in Power Query for Power BI](https://radacad.com/remove-duplicate-doesnt-work-in-power-query-for-power-bi-here-is-the-solution)

### Splitting
* [Split by line breaks in Power Query](https://www.excelguru.ca/blog/2015/10/16/split-by-line-breaks/)
  * Ref. Line feed: #(lf), Carriage return: #(cr), Tab: #(tab)

### Parameters
* [Dynamic M query parameters ](https://docs.microsoft.com/en-us/power-bi/connect-data/desktop-dynamic-m-query-parameters)

### Images
* [Embedding Images in Power BI using Base64](http://sqljason.com/2018/01/embedding-images-in-power-bi-using-base64.html) - sqljason.com

### Web
* [Handling 404–Not Found Errors With Web.Contents() In Power Query And Power BI](https://blog.crossjoin.co.uk/2016/08/09/handling-404-not-found-errors-with-web-contents-in-power-query-and-power-bi/)

-----

### Applied Steps
* Rename (F2)
* Add Description => // in the M Code
* Parametrization 

-----

### Tips
*  Underscore _ references to the current row (record) of the table. e.g., #"Removed Columns" = Table.RemoveColumns(#"Changed Type", List.Select(Table.ColumnNames(#"Changed Type"), each Text.EndsWith(_,"Price"))) // remove all columns that end with "Price"
* Add Leading Zeros; Text.End( "000" & Text.From ([MonthNo] ), 4 ), Text.PadStart( Text.From( [MonthNo] ), 4, "0" )
* Get named range value: Excel.CurrentWorkbook(){[Name=NamedRange]}[Content]{0}[Column1]
* Last Refreshed Date: DateTime.LocalNow()

### Best Practices
* [Best practices when working with Power Query](https://docs.microsoft.com/en-us/power-query/best-practices)
