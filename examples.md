# Examples
This section contains examples for Blueprints & C++ on how to use the plugin.
## Blueprints

## C++
### Creating an HTTP Server
You can easily create an HTTP server with the `UBlueprintHttpServer::CreateHttpServer()` method.
```cpp
// Keep somewhere the HttpServer as an UPROPERTY to prevent
// it from being garbage collected.
UBlueprintHttpServer* HttpServer =  UBlueprintHttpServer::CreateHttpServer();
```

### Creating an HTTPS Server
You can easily create an HTTPS server with the `UBlueprintHttpsServer::CreateHttpsServer()` method.
```cpp
const FString CertLocation = TEXT("path/to/my/cert.pem");
const FString KeyLocation  = TEXT("path/to/my/key.pem");

// We should keep it as an UPROPERTY() somewhere.
UBlueprintHttpServer* const HttpServer = UBlueprintHttpsServer::CreateHttpsServer(CertLocation, KeyLocation);
```

?> `UBlueprintHttpsServer` inherits from `UBlueprintHttpServer`. You should program using the `UBlueprintHttpServer` class to easily switch from HTTP to HTTPS without breaking your code.

### Listening for a Route
To listen for a route, call the method matching the verb of the route. The available verbs are the following:

|Verb|
|:---|
|`GET`|
|`PUT`|
|`POST`|
|`PATCH`|
|`DELETE`|
|`OPTIONS`|

Here is an example listening for two routes:
```cpp
HttpServer

-> Get(TEXT("/data/"), FHttpServerRouteCallback::CreateLambda([](const FBlueprintHttpRequest& Request, FBlueprintHttpResponse& Response) -> void
{
    Response.SetBody(TEXT("Hello World from GET."));
    Response.Send();
}))

// Routes can be regex expressions.
// Here we match all routes of the form "/users/{number}".
-> POST(TEXT("/users/(\+d)"), FHttpServerRouteCallback::CreateLambda([](const FBlueprintHttpRequest& Request, FBlueprintHttpResponse& Response) -> void
{
    Response.SetBody(TEXT("Hello World from POST."));
    Response.Send();
}));
```
