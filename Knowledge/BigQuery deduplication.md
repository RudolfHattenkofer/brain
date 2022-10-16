```sql
select *
from `project.dataset.table`
where 1 = 1 qualify row_number() over (partition by unique_id order by imported_at desc) = 1
```



