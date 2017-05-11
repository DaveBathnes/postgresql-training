GIS data types
==============

| Format | Description |
| ------ | ----------- |
| GeoJSON | Based on JSON, often used in web development. |
| KML | XML based open standard. |
| GML | XML based.  An open spatial data schema to enable interoperability between independent GIS applications and with internet GIS in mind |
| Shapefile | Proprietary and popular ESRI file format. |
| CSV | Data held in traditional CSV files |

GeoJSON
-------

| Aspect | Details |
| ------ | ------- |
| JSON | JavaScript Object Notation.  Based on the JavaScript programming language and ideal for use in web maps.   |
| Lightweight | Text based, and not too much markup |
| Readable | Relatively easy to open in a text editor and read |


KML
---

| Aspect | Details |
| ------ | ------- |
| XML | eXtensible Markup Language.  Based upon XML.  |
| Google | Developed for use with Google Earth, which was originally named Keyhole Earth Viewer |
| Open | KML became an international standard of the Open Geospatial Consortium in 2008 |


Shapefiles
----------

| Aspect | Details |
| ------ | ------- |
| Proprietary | ESRI based standard |
| Common |
| Integration with PostGIS | Easy loading and exporting from PostGIS |


GML
---

| Aspect | Details |
| ------ | ------- |
| XML | eXtensible Markup Language.  Based upon XML.  |
| OS | Used by Ordance Survey as part of certain products such as MasterMap. |
| Tricky | Can be tricky to use and import into databases while maintaining all the data |

CSV
---

| Aspect | Details |
| ------ | ------- |
| Comma separated values | Columns are separated (typically) by commas.  Data that could itself contain a comma is normally wrapped in quotes.  e.g. and address "110 The Laggar, Corsham" |
| Tabular | Can be opened in a variety of software that takes table data, such as Excel and Access |
| WKT | GIS data is often included in CSV through the use of 'Well Known Text' standard, or alternatively simple X/Y values in separate columns |
| Readable | Easy to open in a text editor and read |

```CSV
EX1 1EE,10,N,32,32,18,14,0,15,0,E92000001,E19000002,E18000010,E10000008,E07000041,E05003502,S,POINT (292079 92307)
```
