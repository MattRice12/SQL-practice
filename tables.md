https://www.postgresql.org/docs/9.1/static/sql-altertable.html

## Create table
CREATE TABLE celebs (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL UNIQUE,
  age INTEGER,
  film_id int REFERENCES films(id)
  );

## Change Table Name
  ALTER TABLE [ ONLY ] name [ * ]
      RENAME [ COLUMN ] column TO new_column

## Delete table
DROP TABLE name;


## Rows
  ## Add row to table
  INSERT INTO celebs (id, name, age)
    VALUES (1, 'Justin Bieber', 21);


  ## Update row
  UPDATE celebs
  SET age = 22
  WHERE id = 1;

  ## Delete row
  DELETE FROM celebs
  WHERE twitter_handle IS NULL;

## Columns

  ## Add new column to table
  ALTER TABLE celebs
  ADD COLUMN twitter_handle TEXT;

  ## Change Column Name
    ALTER TABLE name
      RENAME TO new_name

  ## Drop Column
    ALTER TABLE name
      DROP column;
