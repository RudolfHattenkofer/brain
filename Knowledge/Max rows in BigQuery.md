Get the yearly totals, then grab the top yearly

```swift
with transactions as (...
),

yearly as (
  select store_id, extract(year from timestamp) as year, round(sum(meta.price_net) / 100000) as price_net

  from transactions
  left join `sellpick-analytics-general.transactions_source.myindigo_stores` as stores on (stores.store_label = transactions.store_label)

  group by store_id, year
  order by store_id, price_net desc
)

select store_id, year from yearly where (store_id, price_net) in (
  select (store_id, max(price_net)) from yearly group by store_id
)
```

This where query is where the magic happens:



