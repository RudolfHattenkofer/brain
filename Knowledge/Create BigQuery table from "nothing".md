```sql
select * from UNNEST([
	(SELECT AS STRUCT 'column_a' a_name, 'column_b' old_b),
	('column_a 2', 'column_b 2')
])
```

```sql
select 1 as a, 2 as b
```

