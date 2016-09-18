## WITH
The with clauses make it easy to define and use results in a more organized way than subqueries.

    with {subquery_name} as (
      {subquery_body}
    )
    select ...
    from {subquery_name}
    where ...

............................................

    WITH daily_revenue AS (
    	SELECT
    		DATE(created_at) AS dt,
      	ROUND(SUM(price), 2) AS rev
      FROM purchases
      WHERE refunded_at IS NULL
      GROUP BY 1
    )
    SELECT * FROM daily_revenue
    ORDER BY dt;

.............................................


WITH daily_revenue AS (
	SELECT
		DATE(created_at) AS dt,
  	ROUND(SUM(price), 2) AS rev
  FROM purchases
  WHERE refunded_at IS NULL
  GROUP BY dt
),
daily_players AS (
	SELECT
  	date(created_at) AS dt,
  	COUNT(DISTINCT(user_id)) AS players
  FROM gameplays
  GROUP BY 1  	
)
SELECT
	daily_revenue.dt,
  daily_revenue.rev / daily_players.players
FROM daily_revenue
JOIN daily_players
USING (dt);

## USING
When the columns to join have the same name in both tables you can use using instead of on.

E.g., FROM daily_revenue
      JOIN daily_players
      ON daily_revenue.dt = daily_players.dt;

      :is equivalent to:

      FROM daily_revenue
      JOIN daily_players
      USING dt;
