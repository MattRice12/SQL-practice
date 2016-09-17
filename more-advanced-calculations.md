## Case statements to create a temp column, then finding the percentage of each item's revenue in that column

SELECT
	CASE name
	  WHEN 'kale-smoothie'		THEN 'smoothie'
    WHEN 'banana-smoothie'	THEN 'smoothie'
    WHEN 'orange-juice'     THEN 'drink'
    WHEN 'soda'             THEN 'drink'
    WHEN 'blt'              THEN 'sandwich'
    WHEN 'grilled-cheese'   THEN 'sandwich'
    WHEN 'tikka-masala'     THEN 'dinner'
    WHEN 'chicken-parm'     THEN 'dinner'
    ELSE 'other'
  END as category, ROUND(SUM(amount_paid) /
    (SELECT SUM(amount_paid) FROM order_items) * 100, 2) || "%"
as pct
FROM order_items
GROUP BY 1
ORDER BY 2 DESC;

_________________________________________
## COUNTING

# Count how many times an item is ordered

SELECT name, COUNT(DISTINCT(order_id))
FROM order_items
group by 1
order by 1 DESC;

# Count percentage of times an item is ordered over total orders
  (Count distinct orders by item)
  (Divide by total distinct orders)

SELECT name,
	ROUND(1.0 * COUNT(DISTINCT(order_id)) /
  (SELECT COUNT(DISTINCT(order_id)) FROM order_items) * 100, 2) || "%" as pct
FROM order_items
GROUP BY 1
ORDER BY 1 DESC;

# Counting how many times an item is re-ordered
  (Count total distinct orders by item)
  (Divide by how many distinct people order the item)

SELECT name,
	ROUND(1.0 * COUNT(DISTINCT(order_id)) /
	COUNT(DISTINCT(orders.delivered_to)), 2) as reorder_rate
FROM order_items
JOIN orders
ON orders.id = order_items.order_id
GROUP BY 1
ORDER BY 2 DESC;
