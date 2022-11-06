[https://cloud.google.com/compute/docs/reference/rest/v1/urlMaps/update](https://cloud.google.com/compute/docs/reference/rest/v1/urlMaps/update)

[https://cloud.google.com/load-balancing/docs/negs/setting-up-internet-negs](https://cloud.google.com/load-balancing/docs/negs/setting-up-internet-negs)

[Network endpoint groups](https://console.cloud.google.com/compute/networkendpointgroups/list?authuser=0&project=sellpick-prod)

[Load Balancer](https://console.cloud.google.com/net-services/loadbalancing/edit/http/api-gateway?project=sellpick-prod&authuser=0)

[Logging](https://console.cloud.google.com/logs/query;query=resource.type%3D%22http_load_balancer%22%0Aresource.labels.backend_service_name!%3D%22assets%22%0Aresource.labels.backend_service_name!%3D%22api-gateway%22%0Aresource.labels.backend_service_name!%3D%22analytics%22;timeRange=PT5M?project=sellpick-prod&query=%0A)

- Create network endpoint group
   - Type internet
   - Port 443
   - Hostname is project hostname
- Create backend
   - Type Internet network endpoint group
   - Protocol HTTPS
   - Timeout 60

```swift
gcloud config set project sellpick-prod
gcloud compute backend-services create api-tableau-ticket --global --protocol=HTTPS

gcloud beta compute network-endpoint-groups create api-tableau-ticket --network-endpoint-type=internet-fqdn-port --global

gcloud compute network-endpoint-groups update api-tableau-ticket --global --add-endpoint="fqdn=europe-west3-sellpick-prod.cloudfunctions.net,port=443"

gcloud compute backend-services add-backend api-tableau-ticket \
  --network-endpoint-group api-tableau-ticket \
  --global-network-endpoint-group \
  --global

gcloud compute url-maps edit api-gateway --project sellpick-prod
```

```swift
- defaultService: https://www.googleapis.com/compute/v1/projects/sellpick-prod/global/backendServices/api-gateway
  name: path-matcher-2
  pathRules:
  - paths:
    - /v2/analytics/ticket
    routeAction:
      urlRewrite:
        hostRewrite: europe-west3-sellpick-prod.cloudfunctions.net
        pathPrefixRewrite: /tableau-ticket
    service: https://www.googleapis.com/compute/v1/projects/sellpick-prod/global/backendServices/api-tableau-ticket
```

## Serverless NEGs

This does not work at all

[https://cloud.google.com/load-balancing/docs/negs/setting-up-serverless-negs](https://cloud.google.com/load-balancing/docs/negs/setting-up-serverless-negs)

The URL mask thing somehow doesn't work?

```swift
# Create backend
gcloud compute backend-services create api-tableau-ticket --global --project sellpick-prod

# Create NEG
gcloud beta compute network-endpoint-groups create api-sellpick-prod --network-endpoint-type=serverless '--cloud-function-url-mask=europe-west3-sellpick-prod.cloudfunctions.net/<function>' --region europe-west3 --project sellpick-prod

# Add NEG
gcloud beta compute backend-services add-backend api-tableau-ticket --global --network-endpoint-group api-sellpick-prod --network-endpoint-group-region europe-west3 --project sellpick-prod

# Add to load balancer
gcloud compute url-maps edit api-gateway --project sellpick-prod
```



