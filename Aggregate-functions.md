Aggregate functions compute a single result from a set of input values.

# COUNT()
COUNT()  takes the name of a column(s) as an argument and counts the number of rows where the value(s) is not NULL.
  To count every row (incase some columns are null) -- COUNT(\*)

# GROUP BY
GROUP BY is a clause in SQL that is only used with aggregate functions. It is used in collaboration with the SELECT statement to arrange identical data into groups.

E.g., SELECT price, COUNT(\*)
      FROM fake_apps
      GROUP BY price;
        #=> This counts all items at each price level.

        It is usually helpful to SELECT the column you pass as an argument to GROUP BY. Here we select price and COUNT(\*). You can see that the result set is organized into two columns making it easy to see the number of apps at each price.

# SUM()
SUM() takes the column name as an argument and returns the sum of all the values in that column.

E.g., SELECT category, SUM(downloads)
      FROM fake_apps
      GROUP BY category;
        #=> sums all downloads per category.

# MAX()
MAX() takes the column name as an argument and returns the largest value in that column.

E.g., SELECT name, category, MAX(downloads)
      FROM fake_apps
      GROUP BY category;
        #=> Returns the names of the most downloaded apps in each category.


# MIN()
MIN() takes the column name as an argument and returns the smallest value in that column.


# AVG()
AVG() takes a column name as an argument and returns the average value for that column.

E.g., SELECT price, AVG(downloads)
      FROM fake_apps
      GROUP BY price;

# ROUND()
ROUND() takes two arguments, a column name and the number of decimal places to round the values in that column.

E.g., SELECT price, ROUND(AVG(downloads), 2)
      FROM fake_apps
      GROUP BY price;
