PostgreSQL Common Queries
=========================

Brief overview of selecting and querying data in PostgreSQL.  Many of these commands will be similar/identical to commands run in other database servers e.g. SQL Server, Oracle.

Using the pgAdmin 4 GUI
-----------------------

1. In the pgAdmin explorer navigate in the tree to Databases > Training > Schemas > Public > Tables
2. Right click on the postcodes table and select View All Rows

Selecting data
---------------

Select particular columns from the data table.  In the case below, just the postcode and positional quality indicator.

- [SELECT statement documentation](https://www.postgresql.org/docs/current/static/sql-select.html)

```PLpgSQL
SELECT postcode, positional_quality_indicator FROM postcodes;
```

Where clauses
-------------

Filter the data by specifying values that columns must conform to.  In the case below, where the postcode begins 'EX'.

- [WHERE clause featured in SELECT documentation](https://www.postgresql.org/docs/current/static/sql-select.html)

```PLpgSQL
SELECT * FROM postcodes WHERE postcode LIKE 'EX%';
```

Order By
---------

Modify the order in which the data is returned.  In the case below, postcodes sorted in reverse alpabetical order.

- [ORDER BY documentation](https://www.postgresql.org/docs/current/static/queries-order.html)

```PLpgSQL
SELECT postcode FROM postcode ORDER BY postcode DESC;
```

Group By
--------

Commonly used for aggregating and counting data.  In the case below, count postcodes by first two letters.

- [GROUP BY featured in SELECT documentation](https://www.postgresql.org/docs/current/static/sql-select.html)

```PLpgSQL
SELECT SUBSTRING(postcode, 1, 3), COUNT(*) FROM postcodes GROUP BY SUBSTRING(postcode, 1, 3);
```

Update Data
-----------

SQL Update commands will update data in a database table.  It is important to use the WHERE clause with update statements as they will otherwise update every row.  For example, updating a postcode to another postcode:

- [UPDATE statement documentation](https://www.postgresql.org/docs/current/static/sql-update.html)

```PLpgSQL
UPDATE postcodes
SET postcode = 'EX1 4BA'
WHERE postcode = 'EX1 4BB'
```