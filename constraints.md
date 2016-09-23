CREATE TABLE Promotions
(
  id int PRIMARY KEY,
  name varchar(50) <constraint>,
  category varchar(15) NOT NULL UNIQUE
);

    -OR-

CREATE TABLE Promotions
(
  id int,
  name varchar(50),
  category varchar(15) NOT NULL,
  CONSTRAINT unique_category UNIQUE (category)
);

If you want to allow duplicate names or duplicate categories but not both, then use:
  CONSTRAINT unique_name UNIQUE (name, category)

Constraints can:
  Prevent NULL values
  Ensure column values are unique
  Can provide additional validations

#CONSTRAINTS:
  PRIMARY KEY
  NOT NULL
  UNIQUE
