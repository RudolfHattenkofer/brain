- Zuvor <5%
- Letzte Monate schwierig?

Faktoren:
- 
- Hohe Varianz in den Daten "Grundrauschen" ![[Screenshot 2023-02-07 at 14.47.35.png]]
- Wenige Trainingsdaten - Nur ein 1.5 Jahre!!

```
select * from ml.feature_importance(MODEL `sellpick-analytics-ml.familyholding.v1_revenue_daily_base_prev_year`)
```

- 9.2 mit allen Daten
- 10.2 ohne diff_temp, temperature, main_weather, is_sunday, bridging_day_count, daybeforeholiday
- EARLY_STOP no influence