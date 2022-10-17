Yearly theme 2021: Structure

[[What is my purpose?]]

## Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Recipes index]]
[[Coffee]] [[Elbgold]]

[[sell & pick Home]]

## Current
- [[Project management]]
- [[Data Platform]]
- [[Stardew Valley]]
- [[Modern VPN]]

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
