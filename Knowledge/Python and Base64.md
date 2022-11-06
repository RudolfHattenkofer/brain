Python and Base64

```python
import base64

base64.b64encode(message.encode('ascii')).decode('ascii')
base64.b64encode(message.encode('utf-8')).decode('utf-8')
```



