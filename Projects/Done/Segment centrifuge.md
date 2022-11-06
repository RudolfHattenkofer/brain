[Centrifuge: a reliable system for delivering billions of events per day | Segment Blog](https://segment.com/blog/introducing-centrifuge/)

- Unreliable delivery
- Many connections

→ This seems familiar!

Pointers

- Dead letter queue
- Queue per <source/customer, destination>
- DB based

## More realistic implementation

- Simple retry with exponential backoff
- e.g. [https://cloud.google.com/tasks](https://cloud.google.com/tasks)

Queue per



