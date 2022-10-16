transactions-normalized

```swift
gsutil ls -d 'gs://sellpick-transactions-normalized/losteria-*/' > input.txt

# Add * to the end of all folders

# Base command:
bq load --project_id=sellpick-analytics-general --source_format=NEWLINE_DELIMITED_JSON  --noreplace sellpick-analytics-general:transactions_source.losteria 'gs://sellpick-transactions-normalized/losteria-99/2019-*' schema.json

cat input.txt | while read file; do bq load --project_id=sellpick-analytics-general --source_format=NEWLINE_DELIMITED_JSON --noreplace --sync=false sellpick-analytics-general:transactions_source.losteria $file schema.json; sleep 5; done
```



