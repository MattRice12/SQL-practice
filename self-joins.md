## General Retention
SELECT
	DATE(g1.created_at) as dt,
  g1.user_id
FROM gameplays as g1
JOIN gameplays as g2
ON g1.user_id = g2.user_id
ORDER BY 1
limit 100;

## 1 Day Retention 
SELECT
	DATE(g1.created_at) as dt,
  ROUND(100 * COUNT(DISTINCT g2.user_id) /
        COUNT(DISTINCT g1.user_id)) as retention
FROM gameplays as g1
LEFT JOIN gameplays as g2
ON g1.user_id = g2.user_id
AND DATE(g1.created_at) = DATE(DATETIME(g2.created_at, '-1 day'))
GROUP BY 1
ORDER BY 1
limit 100;
