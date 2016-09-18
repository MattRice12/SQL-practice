## DAU -- Daily Active Users
  SELECT
    DATE(created_at),
    COUNT(DISTINCT(user_id)) AS dau
  FROM gameplays
  GROUP BY 1
  ORDER BY 1;


##ARPPU -- Average Revenue Per Purchasing User
Daily ARPPU is defined as the sum of revenue divided by the number of purchasers per day.

SELECT
  DATE(created_at),
  ROUND(SUM(price) / COUNT(DISTINCT(user_id)), 2) as ARPPU
FROM purchases
WHERE refunded_at IS NULL
GROUP BY 1
ORDER BY 1;
