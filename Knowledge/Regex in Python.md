Regex replace in Python

```python
import regex as re

p = re.compile('test')
p.sub('new_text', 'test_string')
# -> 'new_text_string'
```

Matching

```python
import regex as re

p = re.compile('test')
p.search('test_string')
# -> 'new_text_string'
```



