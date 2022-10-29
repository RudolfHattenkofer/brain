BigQuery cannot change a data type easily. Instead the data needs to be queried with an explicit cast and then saved as a new table.

This gets more complicated for nested data structures, as it is not straightforward to replace them. Example for a cast:

```sql
SELECT * REPLACE (
	ARRAY(
		SELECT AS STRUCT * REPLACE(
			(SELECT AS STRUCT meta.* REPLACE(
				cast(meta.nr as int64) as nr
			)) as meta
		) FROM UNNEST(items)) AS items
	)
FROM `project.dataset.table`
```

Remove a repeated record and remove a record

```sql
SELECT

ARRAY(SELECT AS STRUCT * REPLACE(
    (SELECT AS STRUCT meta.* EXCEPT(
        branch_no
    )) as meta
) FROM UNNEST(items)) AS items,

(SELECT AS STRUCT meta.* EXCEPT (customer_count, transaction_count, table_count, price_net)) AS meta,

* EXCEPT (items, meta),

FROM `sellpick-analytics-general.transactions_source.brenner` t
```



