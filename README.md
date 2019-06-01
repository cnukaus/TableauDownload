# TableauDownload
Python script to download workbooks from a Tableau Server.  Developed against version 2.2 of the Tableau Server RESTAPI.

Publishing:
boundary string should be a GUID in header:
https://onlinehelp.tableau.com/current/api/rest_api/en-us/REST/rest_api_concepts_publish.htm
"Each section of the request body begins with a Content-Disposition header and a Content-Type header that describes the type of data in that section. The following example shows the request body for a Publish Workbook request. For this example, the boundary string has been set in the header to 6691a87289ac461bab2c945741f136e6"

Be sure that the Content-Length header is set.

An HTTP response of 500 (Internal Server Error) can mean that a header is missing or incorrect (for example, Content-Length). It can also mean that the payload for Append to File Upload does not include the two required blank lines in the first part of the payload (per the RFC specification for multi-part payloads). 


 turned out it was an encoding problem with the .twbx (zip) file. I changed the encoding before uploading the binary data to iso-8859-1 and it started working


Automating Tableau Workbook Exports Using Python And Tabcmd Command Tool: http://bicortex.com/automating-tableau-workbook-exports-using-python-and-tabcmd-command-tool/


Excel manipulation included

### Excel Trick:
Paste value/format order counts!! value could impact format, so Macro needs topaste value first
only noticed .PasteSpecial xlPasteColumnWidths ~now

#### Pivot table over Pivot (as it's source)
set pivot table option to "Classic pivot table" that each column is a flat field

### Tableau utilities you may not know

https://yupengwu.com/2018/02/21/tableau-wildcard/ 数据解释器 data intepreter to deal with messy Excel formatted header etc

wild card- read multiple data source files 用通配符，跨工作表建立数据源

Primary Group - brings fields from auxilliary data source into primary source Tableau 技巧（99）：用 创建主组 解决数据融合的性能问题


### Power BI tricks:


HOW TO SOLVE if your Power BI table has multi dates, and you want a slice of only Latest date, because you can't filter using date=max(datecolumn)
" A fUNCTION 'MAX' has been used in a true/false exprssion that is used as a table filter expression. This is not allowed. "


use a flag first, SameMonth_Flag = if(month(Table_daily[DateUTC])=month(Omniture_day[Maxdate]),"Y","N")
