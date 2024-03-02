Recently, I explored using UDF (user defined function) in BigQuery
A UDF lets us create a function using SQL expression or Javascript code.

Below code computes the count of records by status in a BigQuery public dataset
```sql
CREATE TEMP FUNCTION status_count(qry STRING)
RETURNS INT64
as (
  (select count(1) from `bigquery-public-data.baseball.schedules` where status = qry)
);

select status_count('closed') as closed_count,
status_count('canceled') as canceled_count,
status_count('unnecessary') as unnecessary_count;
```