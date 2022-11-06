Create new rule, e.g.

```swift
function addAttributes(user, context, callback) {
  context.idToken["https://rbwl.de/counters"] = user.app_metadata.counters || {};
  context.idToken["https://rbwl.de/recent_scans"] = user.app_metadata.recent_scans || [];

  callback(null, user, context);
}
```

Relevant parts:

- Only context.idToken["[https://scope.de/attribute](https://scope.de/attribute)"] is kept
- Function name



