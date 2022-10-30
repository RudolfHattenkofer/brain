
Other notes:
```dataview
list
from "2.2) sell & pick" and -#meeting and !"2.2) sell & pick/Home"
where length(file.inlinks) =0
```


Meetings:
```dataview
list
from #meeting and "2.2) sell & pick"
sort date desc
```

