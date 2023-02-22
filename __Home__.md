
> [!tip] Yearly theme 2023: Foundation
[[2023|2023 - Foundation]]
[[2023-W07]]
[[What is my purpose?]]

> [!note]  Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Coffee]] [[Elbgold]] [[Cafe Bla]]
[[People]]

> [!abstract] Current
[[To Research]] 
[[Logistics of medieval warfare]]
[[Liquidity Management Cashflow]]
[[Short introduction to coffee]]

Projects:
```dataview
LIST
FROM "Projects"
WHERE !startswith(file.path, "Projects/Done") and !startswith(file.path, "Projects/On Hold")
SORT file.mtime DESC
```

> [!example] Work
> [[sell & pick/Home|sell & pick]]


Orphans:
```dataview
list
from "Knowledge"
where length(file.inlinks) =0 and length(file.tags) = 0
```
