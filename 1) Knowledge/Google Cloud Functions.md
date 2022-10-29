[Serverless Load balancing on GCP](./Serverless%20Load%20balancing%20on%20GCP.html)

[Read big files in Cloud Function](./Read%20big%20files%20in%20Cloud%20Function.html)

## Basics

Based on Flask

## Headers

[Request Headers and Responses](https://cloud.google.com/appengine/docs/standard/go/reference/request-response-headers#app_engine-specific_headers)

```swift
request.headers.get("Authorization")
```

## CORS

```swift
def cors_preflight():
    headers = {
        "Access-Control-Allow-Origin": "*",
        "Access-Control-Allow-Methods": "POST",
        "Access-Control-Allow-Headers": "Authorization",
        "Access-Control-Max-Age": "86400",
    }

    return ("", 204, headers)

def main(request)
    if request.method == "OPTIONS":
        return cors_preflight()
```

## Local development

[https://cloud.google.com/functions/docs/functions-framework](https://cloud.google.com/functions/docs/functions-framework)

[GitHub - GoogleCloudPlatform/functions-framework-python: FaaS (Function as a service) framework for writing portable Python functions](https://github.com/GoogleCloudPlatform/functions-framework-python)

```swift
pipenv install --dev functions-framework
pipenv run functions-framework --target=hello --debug
```



