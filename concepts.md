## Relational Database
A relational database is a database that organizes information into one or more tables. Here the relational database contains one table.

## Table
A table is a collection of data organized into rows and columns. Tables are sometimes referred to as relations. Here the table is celebs.

## Column
A column is a set of data values of a particular type. Here id, name, and age are each columns.

## Row
A row is a single record in a table. The first row in the celebs table has:

## Primary Key
A primary key serves as a unique identifier for each row or record in a given table. The primary key is literally an id value for a record.
  By specifying that the id column is the PRIMARY KEY, SQL makes sure that:
    1. None of the values in this column are NULL
    2. Each value in this column is unique
  A table can not have more than one PRIMARY KEY column.

## Foreign Key
A foreign key is a column that contains the primary key of another table in the database. We use foreign keys and primary keys to connect rows in two different tables.
Unlike primary keys, foreign keys do not need to be unique and can be NULL.
