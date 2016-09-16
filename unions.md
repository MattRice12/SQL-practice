
## UNION

Each SELECT statement within the UNION must have the same number of columns with similar data types. The columns in each SELECT statement must be in the same order. By default, the UNION operator selects only distinct values.

E.g., SELECT column_name(s) FROM table1
      UNION
      SELECT column_name(s) FROM table2;

## UNION ALL

UNION --> disallows duplicate values
UNION ALL --> allows duplicate values

These can be useful as subqueries:

E.g., SELECT id, avg(a.sale_price) FROM (
        SELECT id, sale_price FROM order_items
        UNION ALL
        SELECT id, sale_price FROM order_items_historic) AS a
      GROUP BY 1;

## INTERSECT

INTERSECT returns only common rows returned by the two SELECT statements.

E.g., SELECT category FROM new_products
      INTERSECT
      SELECT category FROM legacy_products;

## EXCEPT

EXCEPT returns distinct rows from the first SELECT statement that aren’t output by the second SELECT statement.

E.g., SELECT category FROM legacy_products
      EXCEPT
      SELECT category FROM new_products;
