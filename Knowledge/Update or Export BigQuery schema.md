```other
bq show --format=json project:dataset.table | jq '.schema.fields' > schema.json
cat schema.json
bq update -t --schema=schema.json project:dataset.table
```



