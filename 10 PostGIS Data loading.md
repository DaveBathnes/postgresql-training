PostGIS Data loading
====================

We have already demonstrated loading data into a spatial database by using CSV data where the geographic data is in Well Known Text Form.  Now we need to look at loading various other data formats into PostGIS.

For these exercises we are going to be taking sample data from the Ordnance Survey, available at.

[Ordnance Survey Sample Data](https://www.ordnancesurvey.co.uk/business-and-government/licensing/sample-data/)

*By downloading any of the following datasets you agree to the terms of our Data Exploration Licence. It lets you use the data to research and develop ideas and propositions, create working prototypes, trial as part of your business use for up to 3 months, take part in hackathons and share knowledge.*

For convenience, the data in these exercises is included in the data directory of these notes.

Astun Loader: AddressBase
-------------------------

We will be taking the AddressBase Premium data, available in GML format.

OS GML data is difficult to directly import into PostGIS.  Astun Technology have written an open source [Loader](https://github.com/AstunTechnology/Loader/wiki) for GML data.

Follow the installation instructions [here](https://github.com/AstunTechnology/Loader/wiki/Installation).  Once that it installed we need to use the following configuration in loader.config

```
# Use the OS AddressBase Premium preparation logic
prep_cmd=python prepgml4ogr.py $file_path prep_osgml.prep_addressbase_premium

# OS AddressBase Premium gfs file to specify appropriate schema for the data
gfs_file=../gfs/addressbase_premium.gfs
```

From the python directory Astun Loader has been downloaded to, run the command:

```BatchFile
python loader.py loader.config
```

The data ends up succesfully loaded into our PostGIS database.

Shapefile loader
----------------

PostGIS comes with a convenient shapefile loading tool.

1. Launch PostGIS 2.0 Shapefile and DBF Loader.
2. Fill out the connection details for the database.
3. Select the file.  In this case we'll use county_region.shp (from OS Boundary Line Open).  Modify the SRID to 27700.

Click Import - the data is then imported into a new table called county_region.  We can then check the data has been loaded correctly.

```PLpgSQL
SELECT * FROM county_region WHERE name = 'Somerset County';
``