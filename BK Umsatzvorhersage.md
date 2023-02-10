- Zuvor <5%
- Letzte Monate schwierig?

Faktoren:
- 
- Hohe Varianz in den Daten "Grundrauschen" ![[Screenshot 2023-02-07 at 14.47.35.png]]
- Wenige Trainingsdaten - Nur ein 1.5 Jahre!!

```
select * from ml.feature_importance(MODEL `sellpick-analytics-ml.familyholding.v1_revenue_daily_base_prev_year`)
```

Vorher Situation: 9.3%
8350 - 12.3
12760 - 7.2
13163 - 8.3
13114 - 8.7
13569 - 5.6
15456 - 13.5

https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create-boosted-tree
- initial with all columns: 9.2
- without diff_temp, temperature, main_weather, is_sunday, bridging_day_count, daybeforeholiday: 10.2
- EARLY_STOP: no influence
- every hyperparameter back to zero: 7.9%



```
CREATE OR REPLACE MODEL `sellpick-analytics-ml.familyholding.v4_revenue_daily_base_prev_year`
OPTIONS (MODEL_TYPE = 'BOOSTED_TREE_REGRESSOR',
-- NUM_PARALLEL_TREE = 1,
MAX_TREE_DEPTH = 20,
-- MIN_TREE_CHILD_WEIGHT = 5,
-- LEARN_RATE= 0.15,
-- COLSAMPLE_BYTREE = 0.9,
-- MAX_ITERATIONS = 15,
EARLY_STOP = TRUE,
DATA_SPLIT_METHOD = 'RANDOM',
DATA_SPLIT_EVAL_FRACTION = 0.1,
INPUT_LABEL_COLS = ['price_net_relative'])
AS SELECT

r.store_label,
is_friday,
is_saturday,
is_sunday,
is_weekday,
s.Location_type, -- Autobahn oder Stadt
diff_temp, -- Not relevant for BK customers
temperature, -- Not relevant for BK customers
main_weather,
is_holiday,
-- bridging_day_count,
daybeforeholiday,
is_vacation,
price_net / avg_price_net as price_net_relative,

FROM `sellpick-analytics-ml.familyholding.v2_revenue_daily_base_28_days` r
left join `sellpick-analytics-client.familyholding.stores_v2` s on s.store_label = r.store_label

where avg_price_net != 0 and price_net != 0
and business_day < "2022-12-01"
```



```
select

store_label,
business_day,
price_net as price_net_actual,
predicted_price_net_relative * avg_price_net as predicted_price_net,
temperature,
main_weather,
holiday_label,
bridging_day_count,
daybeforeholiday,
is_vacation,
top_feature_attributions,
CURRENT_TIMESTAMP() AS imported_at,
"v7" as version,

from ML.EXPLAIN_PREDICT(
MODEL `sellpick-analytics-ml.familyholding.v4_revenue_daily_base_prev_year`,
(
select r.* except(holiday_label), is_holiday as holiday_label, s.Location_type
from `sellpick-analytics-ml.familyholding.v2_revenue_daily_base_28_days` r
left join `sellpick-analytics-client.familyholding.stores_v2` s on s.store_label = r.store_label
where business_day between date_sub(current_date(), interval 14 day) and current_date()
),
STRUCT(10 AS top_k_features)
)
```



```with after as (
select
"1" as store_label,
avg(abs(price_net_actual - predicted_price_net) / price_net_actual) diff_after,
from `sellpick-analytics-ml.familyholding.export_20230207_after`
where price_net_actual is not null
and version = "v7"
group by 1
order by 2 desc
),
before as (
select
"1" as store_label,
avg(abs(price_net_actual - predicted_price_net) / price_net_actual) as diff_before,
from `sellpick-analytics-ml.familyholding.export_20230207`
where price_net_actual is not null
group by 1
order by 2 desc
)

select
before.store_label,
diff_before,
diff_after,
diff_after - diff_before,
from before
left join after on (before.store_label = after.store_label)

```


# Proper comparison FH plan
FH plan Dec+Jan by store:
store	diff_fh
14114	11.11%
14569	6.95%
13163	35.96%
8350	18.32%
15456	20.14%
12760	14.73%

Overall	20.46%
Dec		15.7%
Jan		34.6%


s&p model										overall	dec	jan
v1_revenue_daily_base_prev_year	10.3%
v2_revenue_daily_base_prev_year	10.4%
v3_revenue_daily_base_prev_year	9.4%
v4_revenue_daily_base_prev_year 4.9% 3.9% 5.8%
v5_revenue_daily_base_prev_year 22.1% 27.8% 16.3%

Unser Modell mit Basis relativ zum 4-Wochen-Schnitt erzielt eine Genauigkeit von 17.3%.
v6_revenue_daily_base_prev_year 17.3% 19.7% 14.9%

Das selbe Modell mit Basis relativ zum Vorjahres-Schnitt erzielt eine Genauigkeit von 24.1%.
v7_revenue_daily_base_prev_year 24.1% 29% 19%



## Comparison
```
with diffs as (
  select

  store_label,
  business_day,
  price_net_actual,
  predicted_price_net,
  Plan_FH,
  abs(price_net_actual - predicted_price_net) / price_net_actual as diff_sp,
  abs(price_net_actual - Plan_FH) / price_net_actual as diff_fh,
  from `sellpick-analytics-ml.familyholding.export_20230207_after` sp
  left join `sellpick-analytics-ml.familyholding.benchmark_fh_plan` fh on (
    sp.business_day = fh.Datum
    and sp.store_label = concat("familyholding-", cast(fh.Store as string))
  )
  where version = "v6_revenue_daily_base_prev_year"

  order by business_day, store_label
)

-- select
-- store_label,
-- avg(if(business_day between "2022-12-01" and "2022-12-31", diff_sp, null)) as diff_sp_dec,
-- avg(if(business_day between "2023-01-01" and "2023-01-31", diff_sp, null)) as diff_sp_jan,
-- avg(diff_sp) as diff_sp_overall,
-- from diffs
-- group by store_label

-- union all

select
"all",
avg(diff_sp) as diff_sp,
avg(if(business_day between "2022-12-01" and "2022-12-31", diff_sp, null)) as diff_sp_dec,
avg(if(business_day between "2023-01-01" and "2023-01-31", diff_sp, null)) as diff_sp_jan,

from diffs
```

## Generate predictions
```
select

store_label,
business_day,
price_net as price_net_actual,
predicted_price_net_relative * avg_price_net as predicted_price_net,
temperature,
main_weather,
holiday_label,
bridging_day_count,
daybeforeholiday,
is_vacation,
top_feature_attributions,
CURRENT_TIMESTAMP() AS imported_at,
"v7_revenue_daily_base_prev_year" as version,

from ML.EXPLAIN_PREDICT(
  MODEL `sellpick-analytics-ml.familyholding.v7_revenue_daily_base_prev_year`,
  (
    select r.* except(holiday_label), is_holiday as holiday_label, s.Location_type
    -- from `sellpick-analytics-ml.familyholding.v2_revenue_daily_base_28_days` r
    from `sellpick-analytics-ml.familyholding.revenue_daily_relative_to_prev_year` r
    left join `sellpick-analytics-client.familyholding.stores_v2` s on s.store_label = r.store_label
    where business_day between "2022-12-01" and "2023-01-31"
  ),
  STRUCT(10 AS top_k_features)
)
```
## v6_revenue_daily_base_prev_year
-> Based on v2_revenue_daily_base_28_days
```
CREATE OR REPLACE MODEL `sellpick-analytics-ml.familyholding.v6_revenue_daily_base_prev_year`
OPTIONS (MODEL_TYPE = 'BOOSTED_TREE_REGRESSOR',
-- NUM_PARALLEL_TREE = 1,
-- MAX_TREE_DEPTH = 20,
-- MIN_TREE_CHILD_WEIGHT = 5,
-- LEARN_RATE= 0.15,
-- COLSAMPLE_BYTREE = 0.9,
-- MAX_ITERATIONS = 15,
EARLY_STOP = TRUE,
DATA_SPLIT_METHOD = 'RANDOM',
DATA_SPLIT_EVAL_FRACTION = 0.1,
INPUT_LABEL_COLS = ['price_net_relative'])
AS SELECT

r.store_label,
is_friday,
is_saturday,
is_sunday,
is_weekday,
s.Location_type, -- Autobahn oder Stadt
diff_temp, -- Not relevant for BK customers
temperature, -- Not relevant for BK customers
main_weather,
is_holiday,
-- bridging_day_count,
daybeforeholiday,
is_vacation,
price_net / avg_price_net as price_net_relative,

FROM `sellpick-analytics-ml.familyholding.v2_revenue_daily_base_28_days` r
left join `sellpick-analytics-client.familyholding.stores_v2` s on s.store_label = r.store_label

where avg_price_net != 0 and price_net != 0
and business_day < "2022-12-01"
```

## v7_revenue_daily_base_prev_year
-> Based on revenue_daily_relative_to_prev_year
``` 
CREATE OR REPLACE MODEL `sellpick-analytics-ml.familyholding.v7_revenue_daily_base_prev_year`
OPTIONS (MODEL_TYPE = 'BOOSTED_TREE_REGRESSOR',
-- NUM_PARALLEL_TREE = 1,
-- MAX_TREE_DEPTH = 20,
-- MIN_TREE_CHILD_WEIGHT = 5,
-- LEARN_RATE= 0.15,
-- COLSAMPLE_BYTREE = 0.9,
-- MAX_ITERATIONS = 15,
EARLY_STOP = TRUE,
DATA_SPLIT_METHOD = 'RANDOM',
DATA_SPLIT_EVAL_FRACTION = 0.1,
INPUT_LABEL_COLS = ['price_net_relative'])
AS SELECT

r.store_label,
is_friday,
is_saturday,
is_sunday,
is_weekday,
s.Location_type, -- Autobahn oder Stadt
diff_temp, -- Not relevant for BK customers
temperature, -- Not relevant for BK customers
main_weather,
is_holiday,
-- bridging_day_count,
daybeforeholiday,
is_vacation,
price_net / avg_price_net as price_net_relative,

FROM `sellpick-analytics-ml.familyholding.revenue_daily_relative_to_prev_year` r
left join `sellpick-analytics-client.familyholding.stores_v2` s on s.store_label = r.store_label

where avg_price_net != 0 and price_net != 0
and business_day < "2022-12-01"
```