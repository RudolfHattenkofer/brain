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