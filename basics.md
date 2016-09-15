## Update a Row

UPDATE <table_name>
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];

  """
  UPDATE tabs
  SET name = 'BLAH'
  WHERE id = 17;
  """


## Delete a Row

DELETE FROM <table_name>
WHERE [condition];

  """
  DELETE FROM tabs
  WHERE id = 17;
  """

##
