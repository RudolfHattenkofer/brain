```sql
select

branch_id,
timestamp(
  DATETIME(
    business_day,
    TIME(12, 0, 0)
  )
) as purchased_at

from UNNEST(GENERATE_DATE_ARRAY('2017-01-01', current_date(), INTERVAL 1 DAY)) as business_day
cross join (select distinct branch_id from transactions)
```

```sql
select

c_shop_label,
day,
timestamp(
  DATETIME(
    day,
    TIME(cast(hour as int64), cast((hour - floor(hour)) * 60 as int64), 0)
  )
) as purchased_at,

from (
  select day, hour, store_label as c_shop_label
  from UNNEST(GENERATE_DATE_ARRAY('2020-01-01', current_date(), INTERVAL 1 DAY)) as day
  cross join unnest(GENERATE_ARRAY(4, 20, 0.25)) as hour
  cross join (select distinct store_label from `sellpick-analytics-general.transactions_source.lila`)
```

```sql
with daily as (
  SELECT

  'glorious' as chain,
  business_day, branch_id,
  employee_cost, employee_hours,
  revenue,

  FROM `sellpick-analytics-client.glorious.daily`
),

calendar as (
  select
  chain as c_chain,
  branch_id as c_branch_id,
  c_business_day,

  from UNNEST(GENERATE_DATE_ARRAY('2017-01-01', current_date(), INTERVAL 1 DAY)) as c_business_day
  cross join (select distinct chain, branch_id from daily)
)

select
  ifnull(chain, c_chain) as chain,
  ifnull(branch_id, c_branch_id) as branch_id,
  ifnull(business_day, c_business_day) as business_day,
  ifnull(employee_cost, 0.0) as employee_cost,
  ifnull(employee_hours, 0.0) as employee_hours,
  ifnull(revenue, 0.0) as revenue,

from daily
right join calendar on (
  branch_id = c_branch_id and
  c_business_day = business_day
)
```



