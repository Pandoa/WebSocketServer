# Setup
This section will guide you on how to setup WebSocket Server.
If you don't plan to use `C++` or `WSS`, you can directly start using the plugin by following [the examples](examples.md).

## C++ (Optional)
If you plan to use the C++ API, you have to first add the `WebSocketServer` module to your project.
To do so, open `YourProject.Build.cs` and add the following line in the constructor:
```cs
PrivateDependencyModuleNames.AddRange(new string[] { "WebSocketServer" });
```
Once it's done, you can include the C++ files:
```cpp
#include "WebSocketServer.h"  // For the UWebSocketServer class.
#include "WebSocketClient.h"  // For the UWebSocket class.
```

## WSS (Optional)
To use WSS, you have to get a certificate as well as a key file. You can generate a self-signed one for free with OpenSSL.

