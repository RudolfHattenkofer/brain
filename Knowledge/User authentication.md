[Authentication - Tableau](https://help.tableau.com/current/server-linux/en-gb/security_auth.htm)

## Trusted authentication

- Purely IP based security

Not good

- No static IPs in our system

## Javascript authentication

[Tableau JavaScript API Concepts--Authentication - Tableau](https://help.tableau.com/current/api/js_api/en-us/JavaScriptAPI/js_api_concepts_authentication.htm)

Not helpful, just talks about trusted

[Embedding Tableau Server Dashboards into a Website without Prompting for Credentials | Tableau Software](https://kb.tableau.com/articles/howto/embedding-tableau-server-dashboards-into-a-website-without-prompting-for-credentials)

Also only mentions trusted

NO OTHER WAY THAN TRUSTED AUTHENTICATION

## Solution

[Trusted Authentication - Tableau](https://help.tableau.com/current/server/en-us/trusted_auth.htm)

API gateway proxies requests and only forwards the ones with a avlid authentication header.

GET [https://api.sell-pick.com/v1/analytics/ticket](https://api.sell-pick.com/v1/analytics/ticket)

Authentication: api token

Check token, fetch analytics username from API

Get token

POST [https://api.sell-pick.com/v1/analytics/tableau/trusted](https://api.sell-pick.com/v1/analytics/tableau/trusted)

Authentication: xxxxxxxxx

Payload: username

Proxy to

POST [https://10.156.0.9/trusted](https://10.156.0.9/trusted)

Payload: username

Send ticket to user

## Network setup

Set up new network for gateway only

VPC network peering (both ways)

Firewall rules to allow tableau access

Firewall rules to disallow access from internal `10.0.0.0/8`



