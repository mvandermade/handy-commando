Show table status of database:

```SHOW TABLE STATUS FROM <databasename>;```

Show the fields of a table

```DESCRIBE <tablename>;```

Show the size of tables in a database

```
SELECT
  TABLE_NAME AS `table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`,
  TABLE_ROWS AS `table #rows`
FROM
  information_schema.TABLES
WHERE
  TABLE_SCHEMA = "<database name>"
ORDER BY
  (DATA_LENGTH + INDEX_LENGTH)
DESC;
```
