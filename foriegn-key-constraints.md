# Column constraint syntax
  CREATE TABLE Actors (
    id int PRIMARY KEY,
    name varchar(50) NOT NULL UNIQUE,
    country_id int REFERENCES Countries(id)
  );

# Table constraint syntax
  CREATE TABLE Actors (
    id int PRIMARY KEY,
    name varchar(50) NOT NULL UNIQUE,
    country_id int,
    FOREIGN KEY (country_id) REFERENCES countries
  );


# Concepts
  A row in a table containing a FOREIGN KEY that references a missing row in another table is called an
  *orphan record*.

  The *CHECK* constraint is used to validate the value that can be placed in a column.

  * CREATE TABLE Actors (
      id int PRIMARY KEY,
      name varchar(50) NOT NULL UNIQUE,
      salary integer CHECK (salary > 500),
      bonus integer,
      country_id int REFERENCES Countries(id)
      );

# Join Tables
  INSERT INTO Actors_Movies (actor_id, movie_id)
    VALUES (2, 5);
