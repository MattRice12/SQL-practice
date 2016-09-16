## Conditional Aggregates
Conditional Aggregates are aggregate functions that compute a result set based on a given set of conditions.


## CASE / WHEN
Almost every programming language has a way to represent "if, then, else", or conditional logic. In SQL, we represent this logic with the CASE statement

E.g., SELECT
      	CASE
        	WHEN elevation < 250 THEN 'Low'
          WHEN elevation BETWEEN 250 AND 1749 THEN 'Medium'
          WHEN elevation >= 1750 THEN 'High'
          ELSE 'Unknown'
        END AS elevation_tier, COUNT(\*)
      FROM airports
      GROUP BY 1;

## CASE WHEN inside AGGREGATE FUNCTIONS

# COUNT()
E.g., SELECT state,
        COUNT(CASE WHEN elevation < 1000 THEN 1 ELSE NULL END) AS count_low_elevation_airports
      FROM airports
      GROUP BY state;

^^ This counts all airports by state with an elevation less than 1,000.

# SUM()
E.g., SELECT origin,
      			 sum(distance) as total_flight_distance,
             sum(CASE WHEN carrier = 'DL'
                 			THEN distance
                			ELSE 0
                 END) AS total_delta_flight_distance
      FROM flights
      GROUP BY origin;

^^ This sums the total distance from origin, and total distance delta flights traveled from origin

## Percentages
E.g., SELECT origin,
        	   100.0*(SUM(
                CASE
                  WHEN carrier = 'DL' THEN distance
            			ELSE 0
                END)/SUM(distance)) AS percentage_flight_distance_from_delta
      FROM flights
      GROUP BY origin;



E.g., SELECT state,
			100.0 * sum(CASE WHEN elevation >= 2000
                       THEN 1
                       ELSE 0
                  END) / count(\*)  as percentage_high_elevation_airports
      FROM airports
      GROUP BY state;

^^ This finds the percentage of high elevation airports (elevation >= 2000) by state.
