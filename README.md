# metalsmith-excel-markdown
This metalsmith plugin allows you to query excel files using [AlaSQL](https://github.com/agershun/alasql) and then convert them into Markdown tables using [markdown-tables](https://github.com/wooorm/markdown-table).

##Usage

```javascript
var exlmd = require('metalsmith-excel-markdown');
Metalsmith(__dirname)
  .destination('./build')
  .use(exlmd(config({folder: "path/to/excel_files"}))
  .build(function(err) {
    if (err) { throw err; }
  });
```

### Example Source File

```yaml
---
table: 'people.xlsx'
select: 'First_Name, Age, Email'
additional: 'WHERE First_Name = "Patrick" ORDER BY Age ASC
---
#This table shows users first names, their age, and their email.

<TABLE WILL BE APPENDED AT THE BOTTOM OF THE FILE>
```

##General Info

It works by scanning files for 'table', 'select', and/or 'additional' attributes. 

* **table** corresponds to the Excel file to query
* **select** lets you add select statements
  * If no select statement is specified, the default statement is '*'
* **additional** lets you add other SQL statements such as WHERE and ORDER BY
  * If no additional attribute is specified then it is ignored

###Config
A config option ('folder') can also be passed to specify the location of your excel files. By default this is set to 'xlsx/'

###Examples
See the example src files for more examples on how to format the original markdown files. There is also an example repo you can clone [here](https://github.com/patm2013/metalsmith-excelTables)
