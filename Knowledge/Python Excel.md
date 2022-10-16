```python
from openpyxl import load_workbook

wb = load_workbook(filename='doc.xlsx', read_only=True)
sheet1 = wb["Tabelle1"]
rows = sheet1.rows
```

Primitive values for entire row

```python
def extract_values(row):
    return list(map(lambda x: x.value, list(row)))
```

Explore available sheets:

```python
for s in wb.worksheets
    print(s.title)
```

