# SELECT * FROM movies;
selects all columns and rows

# SELECT DISTINCT genre FROM movies;
displays only unique genres; it filters out duplicates
  DISTINCT typically shouldn't be used for multiple selections. Doing so essentially ignores the DISTINCT, and at other times may display nothing.

# WHERE
filters results
  E.g., SELECT name
        FROM customers
        WHERE orders > 5;

\  = equals
\  != not equals
\  > greater than
\  < less than
\  >= greater than or equal to
\  <= less than or equal to


# LIKE
LIKE is a special operator used with the WHERE clause to search for a specific pattern in a column.

# BETWEEN
The BETWEEN operator is used to filter the result set within a certain range. The values can be numbers, text or dates.

# AND OR
AND and OR are special operators that you can use with WHERE to filter the query on two or more conditions.

# ORDER BY
ORDER BY is a clause that indicates you want to sort the result set by a particular column either alphabetically or numerically.

# LIMIT
LIMIT is a clause that lets you specify the maximum number of rows the result set will have.
