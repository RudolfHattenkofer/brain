IoT device authentication

## Google Cloud IoT

- We use Balena for managing the fleet, using Iot Core on top of that would mean a significant overhead

## Service Accounts

- Maximum 100 per project, not scalable

## JWT

## Auth0

[https://auth0.com/machine-to-machine/](https://auth0.com/machine-to-machine/)

[Client Credentials Flow](https://auth0.com/docs/flows/concepts/client-credentials)

Each IoT device is an “Application” that gets access to an “API”.

Pass user information: Auth pipeline > Hooks > Create > Client credentials

```swift
access_token.scope.push('device_id:' + client['name’])
```



