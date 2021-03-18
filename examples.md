# Blueprints
This section contains examples for Blueprints on how to use the plugin.

## Creating a WebSocket Server
To create a WebSocket Server, call the `CreateWebSocketServer` node.
Make sure to store the result in a variable to prevent it from 
being garbage collected.  
![Creates a new WebSocket server](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/CreateServer.png?raw=true)

## Creating a Secure WebSocket Server
To create an WebSocket Server with WSS, call the `Create Secure WebSocket Server` node.  
This node takes 5 parameters:
1. **Key File**: The location of the private key for our WSS Server on disk.
2. **Cert File**: The location of the certificate for our WSS server on disk.
3. **Dh Params File**: An optional DH parameters file.
4. **CA File**: An optional CA file.  

![Creates a new WebSocket Secure server](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/CreateSecureServer.png?raw=true)

## Configuring the Server.
Now that the server is created, you can configure your server. The following nodes are available:

![Configure Nodes](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/Settings.png?raw=true)

## Handling Events
A WebSocket Server offers several events to interact with clients. 

The following image shows the events you can bind.

![WS Events](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/Events.png?raw=true)

!> You must bind the events before calling the `Listen` node.

## Listening for Clients
Once the events are correctly setup, it's time to start listening for WebSocket client connections.

The `Listen` node takes two parameters:
1. **URI**: The location where to reach the WebSocket Server. It supports dynmiac route (i.e. `/path/:id/*` for `/path/{number}/*`).
2. **Port**: The port were the server will be available.

![Listen for Clients](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/Listen.png?raw=true)

## Echo Server Example
The following example shows how to create a simple echo server:  
![Echo Server](https://github.com/Pandoa/WebSocketServer/blob/main/Doc/EchoServer.png?raw=true)
