## Primary Key
Primary Key is a column that serves a unique identifier for row in the table. Values in this column must be unique and cannot be NULL.

## Foreign Key
Foreign Key is a column that contains the primary key to another table in the database. It is used to identify a particular row in the referenced table.

## Joins
Joins are used in SQL to combine data from multiple tables.

___________________________________________________________

## Cross join
Cross joins query multiple tables is to write a SELECT statement with multiple table names separated by a comma. 
  E.g., SELECT albums.name, albums.year, artists.name
        FROM albums, artists

Unfortunately the result of this cross join is not very useful. It combines every row of the artists table with every row of the albums table. It would be more useful to only combine the rows where the album was created by the artist.

## INNER JOIN
The most common type of join in SQL is an inner join.

An inner join will combine rows from different tables if the join condition is true.

E.g., JOIN ... ON

## OUTER JOIN
Outer joins also combine rows from two or more tables, but unlike inner joins, they do not require the join condition to be met. Instead, every row in the left table is returned in the result set, and if the join condition is not met, then NULL values are used to fill in the columns from the right table.

E.g., LEFT JOIN ... ON

## AS
AS is a keyword in SQL that allows you to rename a column or table using an alias. The new name can be anything you want as long as you put it inside of single quotes.
