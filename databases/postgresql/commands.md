# PostgreSQL Commands

## Copy Data From CSV

- comma-separated values sheet that can be imported into a table

```sql
CREATE TABLE revenue (
  store VARCHAR,
  year INT,
  revenue INT,
  PRIMARY KEY (product, year)
);

COPY revenue FROM '~/Documents/revenue.csv' WITH HEADER CSV;
```

## CrossTab Function

- create pivot tables

PREREQ DATA:

| Store | Year | Revenue |
|-------|------|---------|
| Alpha | 2018 | 3287000 |
| Alpha | 2017 | 2190000 |
| Alpha | 2016 | 1637000 |
| Bravo | 2018 | 3399000 |
| Bravo | 2017 | 982000 |
| Bravo | 2016 | 2205000 |
| Charlie | 2018 | 1399000 |
| Charlie | 2017 | 1117000 |
| Charlie | 2016 | 1549000 |
| Delta | 2018 | 2931000 |
| Delta | 2017 | 2065000 |
| Delta | 2016 | 664000 |
| Echo | 2018 | 1047000 |
| Echo | 2017 | 2706000 |
| Echo | 2016 | 1795000 |

- using the data above, we will now create a pivot table:

```sql
CREATE EXTENSION tablefunc;
SELECT * FROM CROSSTAB(
  'SELECT * FROM revenue ORDER BY 1,2'
) AS summary (
  store VARCHAR,
  "2016" INT,
  "2017" INT,
  "2018" INT
);
```

| Store | 2016 | 2017 | 2018 |
|-------|------|------|------|
| Alpha | 1637000 | 2190000 | 3287000 |
| Bravo | 2205000 | 982000 | 3399000 |
| Charlie | 1549000 | 1117000 | 1399000 |
| Delta | 664000 | 2065000 | 2931000 |
| Echo | 1795000 | 2706000 | 1047000 |

## Arrays and JSON

- PostgreSQL supports multi-dimensional arrays

### Example (Posts with Tags)

```sql
CREATE TABLE posts (
  title VARCHAR PRIMARY KEY,
  tags TEXT[]
)

-- Now insert into `posts`

INSERT INTO posts ( title, tags )
  VALUES
  ('PostgreSQL Introduction', '{"postgresql"}'),
  ('Angular and MongoDB', '{"angular","mongodb","javascript"}'),
  ('HTML, CSS and JS Introduction', '{"html","css","javascript"}')
```

- can run a `SELECT` query for any posts that contain the `javascript` tag:

```sql
SELECT * FROM posts WHERE tags @> '{"javascript"}';
```

## JSON Datatype

```sql

-- Setup the table, `sessions`
-- NOTE: session_info has JSON datatype;
CREATE TABLE sessions (
  session_id SERIAL PRIMARY KEY,
  session_info JSON
);

-- now insert some json data
INSERT INTO sessions 
  (session_info)
VALUES
  ('{"app_version": 1.0, "device_type": "Android"}'),
  ('{"app_version": 1.2, "device_type": "iOS"}'),
  ('{"app_version": 1.4, "device_type": "iOS", "mode":"default"}');

-- get device_type from each record in table:
SELECT
  session_info -> 'device_type' AS devices
FROM sessions;

-- casting json data to another data type
SELECT
  COUNT(*)
FROM sessions
WHERE
  CAST(session_info ->> 'app_version' AS decimal) 
  <= 1.0
```

## Perform Statistical Analysis

```sql
CREATE TABLE stats (
  sample_id SERIAL PRIMARY KEY,
  x INT,
  y INT
)

INSERT INTO stats (x,y)
  VALUES
  (1,2),
  (3,4),
  (5,6),
  (7,8),
  (9,10)

-- now perform some analysis:
SELECT
  AVG(x),
  VARIANCE(x),
  STDDEV(x)
FROM stats;

-- find median
SELECT
  PERCENTILE_CONT(0.5)
WITHIN GROUP (ORDER BY x)
FROM stats;

-- 90th percentile
SELECT
  PERCENTILE_CONT(0.9)
WITHIN GROUP (ORDER BY x)
FROM stats;
```

## Working With Shape Data

- can work with geometric data such as points, line segments, polygons and circles

```sql
-- individual points
SELECT
  POINT(0,0) AS "origin",
  POINT(1,1) AS "point"

-- lines
SELECT
  LINE '((0,0), (1,1))' AS "line",
  LSEG '((2,2), (3,3))' AS "line_segment"

-- polygons
SELECT
  POLYGON '((0,0),(1,1),(0,2))' AS "triangle"
  POLYGON '((0,0),(0,1),(1,1),(1,0))' AS "square",
  POLYGON '((0,0),(0,1),(2,1),(2,0))' AS "rectangle";

-- circles
SELECT
  CIRCLE '((0,0),1)' as "small_circle",
  CIRCLE '(0,0),5)' as "big_circle";
```

### Find If Two Lines are Parallel

```sql
SELECT
  LINE '((0,0),(1,1))' ?|| LINE '((2,3),(3,4))';
```

### Find Distance Between To Points

```sql
  SELECT
    POINT(0,0) <-> POINT(1,1);
```

### Two Shapes Overlap

```sql
SELECT
  CIRCLE '((0,0), 1)' && CIRCLE '((1,1), 1)';
```

### Translate A Shape

- move their position

```sql
SELECT
  POLYGON '((0,0),(1,2),(1,1))' + POINT(0,3);
```

[source](https://www.freecodecamp.org/news/postgresql-tricks/)