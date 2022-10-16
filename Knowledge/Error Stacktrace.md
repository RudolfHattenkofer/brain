Error Stacktrace

```python
try: whatever
except Exception as e:
	import traceback
	print("Error occured", e)
	traceback.print_exc()
```



