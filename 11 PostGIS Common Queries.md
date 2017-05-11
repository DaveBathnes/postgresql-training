PostGIS Common Queries
======================

There are many spatial queries that can be run within PostGIS.  A definitive list is held at:

- [PostGIS Functions Index](https://postgis.net/docs/PostGIS_Special_Functions_Index.html)

ST_X
----

Returns the X coordinate of the geometry.

- [ST_X documentation](https://postgis.net/docs/ST_X.html)

```PLpgSQL
SELECT ST_X(geom) FROM postcodes_geo WHERE postcode = 'EX1 1EE';
```

ST_Y
----

Returns the Y coordinate of the geometry.

- [ST_Y documentation](https://postgis.net/docs/ST_Y.html)

```PLpgSQL
select ST_Y(geom) from postcodes_geo where postcode = 'EX1 1EE';
```

ST_Transform
------------

Transforms a geometry into the specified spatial reference system, by ID.  In PostGIS databases spatial reference systems are defined in the spatial_ref_sys table.  ST_Transform relies on PostGIS knowing which SRS the geometry is currently in (in section 9 we used the UpdateGeometrySRID function to set this on a column).

- [ST_Transform documentation](https://postgis.net/docs/ST_Transform.html)

```PLpgSQL
SELECT ST_Transform(geom, 4326) FROM postcodes_geo WHERE postcode  = 'EX1 1EE';
```

Using that to extract the Lng/Lat:

```PLpgSQL
SELECT ST_X(ST_Transform(geom, 4326)), ST_Y(ST_Transform(geom, 4326)) FROM postcodes_geo WHERE postcode  = 'EX1 1EE';
```

ST_DWithin
----------

Returns results that are within a specified distance. In the case below, returns results that are within 100 metres of a certain point.

- [ST_DWithin documentation](https://postgis.net/docs/ST_DWithin.html)

```PLpgSQL
select postcode from postcodes_geo where ST_DWithin(geom, ST_SetSRID(ST_MakePoint(292079, 92307), 27700), 100);
```

ST_Intersects
-------------

Returns results that share the same space.  In the case below, returns postcodes that are within Devon.

- [ST_Intersects documentation](https://postgis.net/docs/ST_Intersects.html)

```PLpgSQL
SELECT postcode FROM postcodes_geo WHERE ST_Intersects(
    geom,
    (SELECT geom FROM county_region WHERE name = 'Devon County')
);
```

ST_Centroid
-----------

Returns the centre point of a geometry.

- [ST_Centroid documentation](https://postgis.net/docs/ST_Centroid.html)

```PLpgSQL
select ST_X(ST_Centroid(wkb_geometry)), ST_X(ST_Centroid(wkb_geometry)) from street where usrn = 14202557
```
