Yearly theme 2021: Structure
[[What is my purpose?]]

## Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Coffee]] [[Elbgold]] [[Cafe Bla]]

[[2.2) sell & pick/Home|sell & pick]] [[2.1) Geardev/scale up/Home|scale up]]
[[People]]

## Current
- [[To Research]]
- [[Landwirtschaft]]
- [[Data Platform]]

Projects:
```dataview
LIST
FROM "Orga/Projects"
WHERE !startswith(file.path, "Orga/Projects/Done") and !startswith(file.path, "Orga/Projects/On Hold")
SORT file.mtime DESC
```

Orphans:
```dataview
list
from "1) Knowledge"
where length(file.inlinks) =0 and length(file.tags) = 0
```
