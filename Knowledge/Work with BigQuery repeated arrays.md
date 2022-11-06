```other
SELECT sum((select sum(ifnull(count, 0.0) * ifnull(price, 0.0)) from unnest(items))) as total,

FROM whereever
```



