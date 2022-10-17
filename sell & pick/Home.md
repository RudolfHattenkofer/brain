
Meetings:
```dataview
list
from #meeting and "sell & pick"
sort date desc
```


Other notes:
```dataview
list
from "sell & pick" and -#meeting and !"sell & pick/Home"
where length(file.inlinks) =0
```
