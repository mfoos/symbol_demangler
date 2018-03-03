### Problem

When reviewing gene lists in Excel, the program overzealously autoconverts certain date-like gene names into dates (among other things). This can happen if someone merely opens the file with Excel and agrees to save change upon closing. [It's a problem](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-1044-7). Converting values back to gene names is non-trivial, because a year is added when the conversion happens.

### Known Issues

* Excel "origin" (the date their software starts counting) was originally different on Mac and Windows machines. Platform upon which the mangling happened will be unknown. [Source](https://support.microsoft.com/en-us/help/214330/differences-between-the-1900-and-the-1904-date-system-in-excel)
* Excel "origin" has a bug in it. [Source](https://support.microsoft.com/en-us/help/214326/excel-incorrectly-assumes-that-the-year-1900-is-a-leap-year)
* When the file is opened, the current year (will be unknown downstream) is incorporated into the new value.
* Excel also interprets RIKEN identifiers with numbers and an "E" (i.e. 2310009E13) as scientific notation numeric
* Genes "MARCH1" and "MARC1" are both converted into the same date (there may be other examples)
* Human, mouse and other organism genomes likely do not use 100% of the same gene names.

### References

[Excel and R](http://r.789695.n4.nabble.com/Difference-in-numeric-Dates-between-Excel-and-R-td3330769.html)
[Leap year error](https://support.microsoft.com/en-us/help/214326/excel-incorrectly-assumes-that-the-year-1900-is-a-leap-year)
[readxl date logic](https://github.com/tidyverse/readxl/blob/master/src/utils.h)
[Existing software solution](http://blogs.nature.com/naturejobs/2017/02/27/escape-gene-name-mangling-with-escape-excel/)
[MS Office Markup Language References](https://www.ecma-international.org/publications/standards/Ecma-376.htm)