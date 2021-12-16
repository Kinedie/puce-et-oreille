# Advanced SQL and Advanced Mysql

## Advanced SQL
### CASE
It's the `if - else` SQL counterpart statement.
``` sql
SELECT <column_name 1>,
  CASE
    WHEN <column_name 2> [comparison : >, <, =, !=, etc] '<value>' THEN '<value to display>'
    WHEN ...
    ELSE '<value to display'>
  END AS '<alias to display>'
FROM <table_name';
```

## Advanced Mysql
### LOCK TABLES
#### READ constraint
#### WRITE constraint
### EXISTS condition
#### IF EXISTS
#### IF NOT EXISTS
### What is a Common Table Expression (or CTE) ?
### What are triggers ?

