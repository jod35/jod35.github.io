# Learn How to Use WebSockets with Python

## What Are WebSockets?

This guide will help you build real-time applications using Python and WebSockets. So, what are WebSockets?

WebSockets are a network protocol that enables real-time, two-way communication between a client and a server over a single TCP connection. Unlike traditional HTTP requests, WebSockets allow continuous data exchange without repeated requests, making them ideal for applications like chat systems or live data updates.

## How Do WebSockets Work?

WebSockets operate through the following steps:

1. **Opening Handshake**  
   The client sends an HTTP **GET** request with a WebSocket upgrade header. The server responds with a **101 Switching Protocols** status code if successful, establishing the WebSocket connection.

2. **Exchanging Messages**  
   After the handshake, the client and server can send data or control messages back and forth in real time over the persistent connection.

3. **Closing Handshake**  
   When either the client or server terminates the connection, a closing handshake is performed, and the connection is closed.

## Implementing a WebSocket Server Using Python

In this section, we'll create a simple WebSocket server using the Python [websockets](https://websockets.readthedocs.io/en/stable/index.html) library.

### Installing the WebSockets Library

Set up a virtual environment and install the `websockets` library:

```bash
python -m venv env
source env/bin/activate  # On Windows, use: env\Scripts\activate
pip install websockets
```

### Creating the WebSocket Server

We'll define a function to handle client connections. Create a file named `server.py` with the following code:

```python
from websockets.asyncio.server import ServerConnection

async def say_hello(websocket: ServerConnection):
    await websocket.send("Hello World!")
```

This defines an asynchronous `say_hello` function that takes a `websocket` object (representing a client connection) and sends the message `"Hello World!"` to the client. The `await` keyword ensures the send operation is asynchronous.

To serve this function, we need to set up a WebSocket server. Update `server.py` as follows:

```python
import asyncio
from websockets.asyncio.server import ServerConnection, serve

async def say_hello(websocket: ServerConnection):
    await websocket.send("Hello World!")

async def main():
    async with serve(say_hello, "localhost", 8005) as server:
        await server.serve_forever() # Run the server indefinitely
```

In this code, we import `asyncio` and the `serve` function from `websockets.asyncio.server`. We define an asynchronous `main` function that starts the WebSocket server using `serve`, passing the `say_hello` handler, `"localhost"` as the host, and `8005` as the port. 

The server is kept running indefinitely by calling the `server.serve()` method. To execute the asynchronous `main` function, we use `asyncio.run`. Below is the complete `server.py` file:

```python
import asyncio
from websockets.asyncio.server import ServerConnection, serve

async def say_hello(websocket: ServerConnection):
    await websocket.send("Hello World!")

async def main():
    async with serve(say_hello, "localhost", 8005) as server:
        await server.serve_forever()  # Run the server indefinitely

if __name__ == "__main__":
    asyncio.run(main())
```

### Explanation of the Server Code
The server code consists of a handler function, `say_hello`, which defines the behavior for each client connection by sending a `"Hello World!"` message to the client. The `main` function sets up the server using the `serve` function, which creates a WebSocket server bound to `localhost` on port `8005`.

The use of the `async with` context manager ensures that the server is properly cleaned up when it shuts down. The server is started by calling `asyncio.run(main())`, which runs the event loop and keeps the server running until it is interrupted (for example, by pressing Ctrl+C). By default, the server listens only on the local machine at the specified port.

### Running the Server
To test the server:
1. Save the code in `server.py`.
2. Activate your virtual environment and ensure `websockets` is installed.
3. Run the server with:
   ```bash
   python server.py
   ```
4. The server will listen for WebSocket connections at `ws://localhost:8005`.

You can test it using a WebSocket client (e.g., a browser with JavaScript or a Python client using `websockets`). Upon connecting, the client will receive the `"Hello World!"` message.
