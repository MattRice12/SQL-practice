## Subqueries
Used to complete an SQL transformation by nesting one query within another query.

## Non-correlated Subquery
A non-correlated subquery is a subquery that can be run independently of the outer query and as we saw, can be used to complete a multi-step transformation.

E.g., SELECT *
      FROM flights
      WHERE origin IN (
      	SELECT code
      	FROM airports
      	WHERE elevation < 2000);


## Correlated Subquery
In a correlated subquery, the subquery can not be run independently of the outer query. The order of operations is important in a correlated subquery:
  1. A row is processed in the outer query.
  2. Then, for that particular row in the outer query, the subquery is executed.

E.g., SELECT a.dep_month,
      			 a.dep_day_of_week,
             AVG(a.flight_distance) AS average_distance
             FROM (
              SELECT dep_month,
                     dep_day_of_week,
               		   dep_date,
                     SUM(distance) AS flight_distance
              FROM flights
              GROUP BY 1, 2, 3
              ) a
      GROUP BY 1,2
      ORDER BY 1,2;

The sub-query sums the flight distance, grouped by date;
The main-query averages the summed flighted distances, grouped by date.




E.g., SELECT id, distance, carrier
      FROM flights AS f
      WHERE distance < (
        SELECT AVG(distance)
        FROM flights
        WHERE carrier = f.carrier)
      ORDER BY carrier;

Sub-query: Finds the average distance for each carrier
Main-query: Selects all flights flying less distance than their carriers' average.




E.g., SELECT carrier, id,
         (SELECT COUNT(\*)
          FROM flights f
          WHERE f.id < flights.id
          AND f.carrier=flights.carrier) + 1
      AS flight_sequence_number
      FROM flights;

Sub-query: Counts the flights by carrier and where flights are unique
  #??? f.id < flights.id ???
  #f.carrier = flights.carrier --> sorts by carrier, right?
Main-query: Selects all flights
