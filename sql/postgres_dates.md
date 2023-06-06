# PostgreSQL Dates

Coming from MSQL, PostgreSQL date functions make so much more sense. 


Add dates:

```SQL

SELECT date '2023-01-01' + 10;

--'2023-01-11'

SELECT current_date - 7;

--This day last week

```

Select for specific months, years or age:


```SQL

SELECT * from some_table t where date_part('year',t.date) >= 2022 AND date_part('month',t.date) = 01;

--Data from some_table after 2022 in january


select t.docid, age(t.date) from some_table t where age(t.date) < '1 year 1 mons 10 days' limit 100;

--Data younger than 1 year, 1 months and 10 days

```

Also OVERLAPS is supported!

```SQL

SELECT (MAX(t.docdate), MIN(t.docdate)) OVERLAPS
       (DATE '2020-01-01', DATE '2021-01-01') from some_table t ;
       
-- Result: true if some_table has dates that overlap '2020-01-01' to  '2021-01-01'.

```

PostgresSQL 15 docs here: https://www.postgresql.org/docs/15/functions-datetime.html
