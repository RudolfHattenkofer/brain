Yearly theme 2021: Structure
[[What is my purpose?]]

## Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Coffee]] [[Elbgold]] [[Cafe Bla]]

[[sell & pick/Home|sell & pick]]

[[People]]

## Current
- [[To Research]]
- [[Landwirtschaft]]
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



Buttons:
```button
name New Meeting
type note
action "Orga/Templates/sell & pick Meeting"
```
^ button-create-sp-meeting