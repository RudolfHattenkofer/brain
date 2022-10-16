Send list to PubSu

```python
from google.cloud import pubsub
import json

publisher = pubsub.PublisherClient()
topic = "projects/{project_id}/topics/{topic}".format(
	project_id=PROJECT_ID,
	topic="topic",
)

def send(data):
	for d in data:
		publisher.publish(
			topic,
			json.dumps(d).encode("utf-8")
		).result()
```



