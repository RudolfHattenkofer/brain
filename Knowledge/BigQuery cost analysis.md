[billing dataset](https://console.cloud.google.com/bigquery?authuser=0&project=sellpick-analytics-client&p=sellpick-prod&d=billing&t=gcp_billing_export_v1_00739F_1252E7_073BF6&page=table)

```swift
SELECT

sum( protopayload_auditlog.servicedata_v1_bigquery.jobGetQueryResultsResponse.job.jobStatistics.totalBilledBytes) / 1024 / 1024 / 1024,
tables.datasetId, tables.tableId

FROM `sellpick-analytics-general.sp_billing.cloudaudit_googleapis_com_data_access`
, unnest(protopayload_auditlog.servicedata_v1_bigquery.jobGetQueryResultsResponse.job.jobStatistics.referencedTables) as tables
group by tables.datasetId, tables.tableId
```



