What is a WebSocket?
At its core, a WebSocket is a communication protocol that provides full-duplex communication channels over a single, long-lived TCP connection.

Unlike the traditional HTTP model—where the client must ask for data and the server only responds when asked—WebSockets allow the server to push information to the client spontaneously the moment it becomes available.

Why do we need them?
Before WebSockets, developers relied on hacks like Long Polling, where the client constantly asks the server, "Anything new yet?" dozens of times a minute. It was inefficient, laggy, and drained battery life.

WebSockets solved this by:

Eliminating Latency: No need to wait for a new request header to be processed.

Reducing Server Load: The server doesn't have to keep opening and closing TCP connections for every single data update.

Enabling Real-Time Apps: Essential for things like live stock tickers, multiplayer games, chat applications, and collaborative document editing.

How it works: The Lifecycle
The magic happens in three phases:

The Handshake: It starts as a standard HTTP request. The client sends a special "Upgrade" header to the server. If the server supports WebSockets, it replies with a 101 Switching Protocols status.

The Open Connection: The HTTP connection is "upgraded" to a persistent WebSocket connection. The TCP socket stays open.

Data Transfer: Both parties can send "frames" of data whenever they want. This is full-duplex, meaning both sides can "talk" at the same time without waiting for the other to finish.

Comparison at a Glance

Feature,HTTP,WebSockets
Connection,Request-Response (Short-lived),Persistent (Long-lived)
Direction,"Unidirectional (Client asks, Server gives)",Full-Duplex (Both send/receive)
Overhead,High (New headers for every call),"Very Low (Initial handshake, then tiny frames)"
State,Stateless,Stateful
