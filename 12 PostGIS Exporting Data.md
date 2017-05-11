PostGIS Exporting Data
======================

Shapefile exporter
------------------

The Shapefile Loader we used in the data loading section can also be used to export data to shapefile.

1. Launch PostGIS 2.0 Shapefile and DBF Loader.
2. Fill out the connection details for the database.
3. Change from Import to Export.
4. Click Add Table.  Select the Table (e.g. postcodes_geo) and click OK.
5. Click Export and select an output folder.

The shapefile files (cpg,dbf,prj,shp,shx) will be exported into the folder.

Shapefile exporter command line
-------------------------------

The shapefile exporter allows you to select tables and database views to export these as shapefiles.  But what about custom database queries that either select certain fields, or that do some geoprocessing (such as cookie-cutting data).  These could be transferred into a new table but they can also be exported to shapefile using a command line tool pgsql2shp.

The tool is installed as part of PostGIS and is installed at C:\Program Files\PostgreSQL\9.6\bin\pgsql2shp.exe

- [pgsql2shp documentation](http://postgis.net/docs/manual-1.5/ch04.html#id361651)

The tool can be used to run complex SQL commands.  These could be scheduled and set to run whenever appropriate.

```BatchFile
"C:\Program Files\PostgreSQL\9.6\bin\pgsql2shp.exe" -f "C:\output" -u postgres training "select distinct a.* from ((select * from postcodes_geo where ST_DWithin(geom, ST_SetSRID(ST_MakePoint(292079, 92307), 27700), 100)) union all (select * from postcodes_geo where ST_DWithin(geom, ST_SetSRID(ST_MakePoint(292279, 92507), 27700), 100))) a"
```

COPY
----

We have primarily used the COPY command in PostgreSQL to import data, but it can also be used for exporting data.  It is best used for exporting tabular (CSV) data.

```PLpgSQL
COPY postcodes_geo to 'C:\output\postcodes_geo.csv' CSV;
```

That's exporting a single table to a CSV file, the same can be done with a custom query.

```PLpgSQL
COPY (SELECT postcode, ST_X(geom), ST_Y(geom) FROM postcodes_geo) TO 'C:\output\postcode_custom.csv' CSV;
```