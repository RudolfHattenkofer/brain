Yearly theme 2021: Structure
[[What is my purpose?]]

## Topics
[[All topics]]
[[Tech]] [[Python]] [[BigQuery]]
[[Coffee]] [[Elbgold]] [[Cafe Bla]]

[[sell & pick/Home|sell & pick]]
```button
name New Meeting
type note(<% tp.date.now("YYYY-MM-DD HH-MM") %>) template
action Meeting
templater True
```
```button
name New s&p Meeting
type note(<% tp.date.now("YYYY-MM-DD HH-MM") %>) template
action sell & pick Meeting
templater True
```

[[People]]

```note-blue
Test
```

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

^button-general


^button-sp
