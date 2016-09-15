
## Create table
CREATE TABLE celebs (
  id INTEGER PRIMARY KEY,
  name TEXT,
  age INTEGER
  );


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
