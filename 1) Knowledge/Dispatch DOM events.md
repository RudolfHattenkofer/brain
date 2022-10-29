```swift
var event = document.createEvent('Event');
event.initEvent("eventName", bubbles, cancellable);
document.ddispatchEvent(event);
```

```swift
document.addEventListener("eventName", callback);
```



