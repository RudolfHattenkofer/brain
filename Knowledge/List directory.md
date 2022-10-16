List directory

```other
import os

directory = 'data'
for f in sorted(os.listdir(directory)):
    filename = '{}/{}'.format(directory, f)
    open(filename)
```

List subdirectories

```python
from glob import glob

for filename in glob("data/**/*.json", recursive=True):
    print(filename)
    content = open(filename).read()
```



