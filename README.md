# metalsmith-excel-markdown
Metalsmith plugin to query excel files with Alasql and convert to markdown

## About
This metalsmith plugin allows you to query excel files using AlaSQL and then convert them into Markdown tables using markdown-tables.

##Usage

###General
It works by scanning files for 'table', 'select', and/or 'additional' attributes. 

* The table attribute corresponds to the Excel file to query
* The select attribute lets you add select statements
  * If no select statement is specified, the default statement is '*'
* The additional attribute lets you add other SQL statements such as WHERE and ORDER BY
  * If no additional attribute is specified then it is ignored

###Config
A config option ('folder') can also be passed to specify the location of your excel files. By default this is set to 'xlsx/'

### Metalsmith initialization

```javascript
var exlmd = require('metalsmith-excel-markdown);
Metalsmith(__dirname)
  .destination('./build')
  .use(exl(config({folder: "path/to/excel_files}))
  .build(function(err) {
    if (err) { throw err; }
  });
```

See the example src files for examples on how to format the original markdown files. There is also an example repo you can clone [here](https://github.com/patm2013/metalsmith-excelTables)
