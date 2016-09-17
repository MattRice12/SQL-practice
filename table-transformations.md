
## Timestamps
DATE() -- shows date
TIME() -- shows time
DATETIME() -- shows date and time

## Increment time
DATETIME(time1, +X hours, Y minutes, Z days): Increments the specificed column by a given number of hours, minutes, or days.

E.g.,
      SELECT DATETIME(delivery_time, '+5 hours', '20 minutes', '2 day') as package_times
      FROM baked_goods;



_______________________
## Math

SELECT ( 1 + 2 );
#=> 3

SELECT CAST(10 AS REAL) / 3;
#=> 3.33333333333

SELECT ROUND(3.33333, 1);
#=> 3.3



#MAX(n1,n2,n3,...)
Returns the greatest value in the set of the input numeric expressions.

#MIN(n1,n2,n3,...)
Returns the least value in the set of the input numeric expressions.

______________________
## String Manipulation

# Concatenation
  SELECT string1 || ' ' || string2;

# REPLACE()
  REPLACE(string, from_string, to_string);
