```SQL
SELECT
  name,
  car.id AS car_id,
  car.model AS car_model,
  manufacture.year AS manufacture_year,
  ARRAY(
  SELECT
    AS STRUCT id,
    TIMESTAMP_ADD(date, INTERVAL 3 HOUR) AS date
  FROM
    UNNEST(purchase)) AS purchase
FROM
  sample.semi_structured_hw
CROSS JOIN
  UNNEST(car) AS car
INNER JOIN
  UNNEST(manufacture) AS manufacture
ON
  car.id=manufacture.id
```
