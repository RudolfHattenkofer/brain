- Download as CSV

   This snippet makes it possible to download the results as a CSV. The columns have to be specified separately because nested fields cannot be downloaded to a local file.

```sql
SELECT
event_id, tag_id, source.captcha_action, source.human_score, meta.partner as partner_id, meta.location_name, meta.location_latlong, meta.user_id, source.captcha_timestamp, source.ip
FROM `user-scan-7a2e1.scans.unique_pings`
where tag_id like 'ct%'
```

- Usages for specific timeframe and URL range

```sql
SELECT
event_id,
tag_id,
substring(tag_id, 5) as tag_nr,
source.captcha_action, source.human_score,
meta.partner as partner_id, meta.location_name, meta.location_latlong, meta.user_id,
source.captcha_timestamp, source.ip
FROM `user-scan-7a2e1.scans.unique_pings`

-- Only Cups
where tag_id like 'ct%'

-- Only week of the 2020-11-02
and timestamp > '2020-11-02' and timestamp < '2020-11-16'

-- Only tags from 1111 to 11sv (caution: alphanumeric notation!)
and substring(tag_id, 5) >= '1111' and substring(tag_id, 5) <= '11sv'
```

- Multiple ranges

```sql
SELECT
event_id,
tag_id,
substring(tag_id, 5) as tag_nr,
source.captcha_action, source.human_score,
meta.partner as partner_id, meta.location_name, meta.location_latlong, meta.user_id,
source.captcha_timestamp, source.ip
FROM `user-scan-7a2e1.scans.unique_pings`
-- Only Cups
where tag_id like 'ct%'
-- Only week of the 2020-11-02
and timestamp > '2020-11-23' and timestamp < '2020-12-24'
-- Only tags from 1111 to 113t and tags from 11ex to 11ho (caution: alphanumeric notation!)
and
(
  (substring(tag_id, 5) >= '1111' and substring(tag_id, 5) <= '113t')
  or
  (substring(tag_id, 5) >= '11ex' and substring(tag_id, 5) <= '11ho')
)
```



