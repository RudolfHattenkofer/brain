Yearly theme 2021: Structure

[[What is my purpose?]]

## Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Recipes index]]
[[Coffee]] [[Elbgold]] [[Cafe Bla]]

[[sell & pick/Home|sell & pick]]
[[People]]

[[To Research]]

## Current
- [[Stardew Valley]]
- [[Landwirtschaft]]
- [[Knowledge Management]]
- [[Modern VPN]]
- [[Project management]]
- [[Data Platform]]

Projects:
```dataview
LIST
FROM "Projects"
WHERE !startswith(file.path, "Projects/Done") and !startswith(file.path, "Projects/On Hold")
SORT file.mtime DESC
```

Orphans:
```dataview
list
from "Knowledge"
where length(file.inlinks) =0 and length(file.tags) = 0
```
