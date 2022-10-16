0 setup

## Hook to add full name to profile

[https://manage.auth0.com/dashboard/eu/rebowl/hooks](https://manage.auth0.com/dashboard/eu/rebowl/hooks)

```swift
module.exports = function(client, scope, audience, context, cb) {
  var access_token = {};
  access_token.scope = scope;

  access_token.scope.push('device_id:' + client['name'])

  cb(null, access_token);
};
```

## Add rule for scans in token

[https://manage.auth0.com/dashboard/eu/rebowl/rules](https://manage.auth0.com/dashboard/eu/rebowl/rules)

```swift
function addAttributes(user, context, callback) {
  var meta = (user.app_metadata || {});
  context.idToken["https://rbwl.de/counters"] = meta.counters || {};
  context.idToken["https://rbwl.de/recentScans"] = meta.recent_scans || [];

  callback(null, user, context);
}
```



