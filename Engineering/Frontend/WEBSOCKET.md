---
tags: engineering/frontend, frontend, websocket, protocols, browser api
author: Bui Ngoc Nam Anh
github_id: tonible14012002
date: 2023-5-10
---
## What is websocket
Previously, creating web applications that need bidirectional require a HTTP polling for updating the data from the server. 
This result in lots of problems such as high overhead, latency, not-truthly realtime.

Websocket is a simple solution that is invented to solve those problems. Websocket maintain one single TCP connection for traffic in both directions.

Websocket currently can work over HTTP port 80, 443 and as proxies as it is designed for addressing the other existing bidirectional HTTP technologies so that take advantage of existing HTTP infrastructure.

## The Protocol Overview
### Handshake
A HTTP Handshake is preformed before update to websocket connection. The client makes a GET request to the server with an upgrade header. The server then reponse with status 101 to upgrade the current connection to be websocket connection. Otherwise, the client has to end the connection.

Example handshake
#### From client
```javascript
GET /chat HTTP/1.1
    Host: server.example.com
    Upgrade: websocket
    Connection: Upgrade
    Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
    Origin: http://example.com
    Sec-WebSocket-Protocol: chat, superchat
    Sec-WebSocket-Version: 13
```
- `Sec-WebSocket-Key` is to ensure the server support WebSocket protocol, the key is generated random to preven proxy server to cache and follow the communication
#### From server
```javascript
HTTP/1.1 101 Switching Protocols
    Upgrade: websocket
    Connection: Upgrade
    Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
    Sec-WebSocket-Protocol: chat
```
- `Sec-WebSocket-Accept`: is a response key to show server acceptance, the server first take the value of `Sec-Websocket-Key`, append `"258EAFA5-E914-47DA-
   95CA-C5AB0DC85B11"` *(Globally Unique Identifier)* and then hashed with SHA-1

### Data Transfer
After the handshake was successfull, each side can start sending or receiving data. The data unit in websocket is `message`.

Websocket use sequantial `frames` for transfering message instead of `streaming`. This result in each side can exchange data independently without any blocking.

#### *Framing
A `Frame` is a small `header` + `payload`, the payload is similiar to other application data such as body of a HTTP message. 
In most basic form of Websocket protocols include 2 type of frames:
- Non-control frame:
  + `text` - denotes sending `utf-8` encoded bytes
  + `binary` - sending raw bytes
  + `continue` - sending a continuation fragment of previous message
- Control frame:
  + `close` - denote that wanting to close, or responding to a close
  - `ping`
  - `pong`

*[Read detail here](https://datatracker.ietf.org/doc/html/rfc6455#section-5.2)*

#### *Authentication
The protocols it self donot specify an authentication method. User can use any other machanism used in HTTP such as TLS authentication, cookies or authentication Header *(Except for browser client, Websocket api donot provide a way to modify the client handshake Header)*.

#### *Websocket URI
```
ws-URI = "ws:" "//" host [ ":" port ] path [ "?" query ]
wss-URI = "wss:" "//" host [ ":" port ] path [ "?" query ]
```
Note that the differences between `ws` and `wss`is:
- **`ws` use `HTTP` for handshake while `wss` use `HTTPS`**
- Default port for `ws` is 80 and `wss` is port 443

## Websocket Browser Api
The browser provide an Api for creating and managing Websocket connection as well as exchange messages with a websocket server.

### Open WebSocket connection
Create new Websocket, it will start connecting immediately. 
```typescript
const socket = new WebSocket("ws://localhost:8080")
```
### WebSocket Events
There are totally 4 events
```typescript
// Connection opened
socket.addEventListener("open", (event) => {});
// Receive messages from server
socket.addEventListener("message", (event) => {});
// Connection Error
socket.addEventListener("error", (event) => {})
// After connection closed
socket.addEventListener("close", (event) => {})
```
### Data Transfer
The API browser only allow to work directly with birany and text data.
#### Sending message
`socket.send(body)` method allow sending a message to the server. The `body` argument can be a `string` or `binary format type` such as `ArrayBuffer`, `Blob`.

#### Receiving message
Access `event.data` for incomming message
```typescript
socket.onmessage = (event) => {
  console.log(event.data)
}
```
- For Text message, `event.data` will alway be `string`
- For `binary type` message, user can choose between `Blob` and `ArrayBuffer` by assign `WebSocket.binaryType='arraybuffer` *(default is `blob`)* then `event.data` will be the approriate type

```typescript
socket.binaryType = "arraybuffer"
socket.onmessage = (event) => {
  if (event.data instanceof ArrayBuffer) {
    // Handling binary message
    return
  }
  // Handling String message
}
```
### Rate Limiting
When user has a slow network connection. After calling `WebSocket.send(...)` the data will be buffered in memory and will be sent out as soon as connection get better

`WebSocket.bufferedArmount` return the amount of data queued using `call()` but not yet send out to the network. *This value will not reset to zero if connection close.*

```typescript
if (socket.bufferedAmount === 0) {
  socket.send(moreData())
}
```

### Close Connection
For sending `close frame` from browser WebSocket, simply call `WebSocket.close(code, reason)`
```typescript
socket.close(1000, "Complete") // both argument is optional
socket.onclose = (event) => {
  const { code, reason, wasClean } = event
  console.log({code, reason, wasClean})
  // { code: 1000, reason: "Complete", wasClean: true }
}
```
#### *Common code
- 1000 - normal closure (default)
- 1006 - connection was lost (this code cannot set manually, connection close abnormally by the browser and event go to `WebSocket.onerror`)
- 1001 - the party is going away (server shutting down, browser leave the page)
- ...

## Connection State
User can access `WebSocket.readyState` for getting the current state of a WebSocket instance
- `0`: CONNECTING - socket created but connection is not open yet
- `1`: OPEN - Connection is open and ready to communicate 
- `2`: CLOSING - Connection is in closing process
- `3`: CLOSED - Connection is closed or could not be opend