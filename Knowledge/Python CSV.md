## Read

```python
import csv

f = open('path.csv')
data = list(csv.reader(f, delimiter=','))
```

Encoding wrong?

```python
import csv

f = open('path.csv', encoding='windows-1252')
data = list(csv.reader(f, delimiter=';'))
```

Weird shit going on? Don’t panic:

```python
import csv
from io import StringIO

contents = open('{}'.format('data/input.csv'), 'r', encoding='windows-1252').read()
contents = contents.replace('ä', 'ä')

data = list(csv.reader(StringIO(contents), delimiter=';'))
```

## Write

```python
import csv

out = open('file.csv', 'w')
writer = csv.writer(out)

for x in xs:
    writer.writerow([x, 1, 'test'])

out.close()
```



