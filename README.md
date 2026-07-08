# Echo Server

A simple TCP echo server and client written in C using POSIX sockets. The server accepts a connection from a client, receives a message, and sends the same message back (its that simple).

This whole project is just one of the Phase to build my custom NAS

**NOTES: All of the rant below is by GPT as i'll uplode my notes so if anyone intrested can look that, but TL;DR is below**

## Features

* TCP client/server communication
* IPv4 sockets
* Shared utility functions in `common.c`
* Simple example of:

  * `socket()`
  * `bind()`
  * `listen()`
  * `accept()`
  * `connect()`
  * `read()`
  * `write()`
  * `close()`

## Project Structure

```text
.
├── client.c      # TCP client
├── server.c      # TCP server
├── common.c      # Shared helper functions
├── common.h      # Shared declarations and constants
└── README.md
```

## Requirements

* GCC
* Linux or another POSIX-compatible operating system

## Build

Compile the server:

```bash
gcc -Wall -Wextra server.c common.c -o server
```

Compile the client:

```bash
gcc -Wall -Wextra client.c common.c -o client
```

## Running

### 1. Start the server

```bash
./server
```

The server will begin listening on port `5000`.

### 2. Start the client

Open another terminal and run:

```bash
./client
```

Example output:

Server terminal:

```text
yohoo
```

Client terminal:

```text
server: yohoo
```

## Shared Utilities

The project uses `common.c` and `common.h` to avoid duplicated code.

Current shared functionality includes:

* `createSocket()` – Creates a TCP socket.
* `sendMessage()` – Sends a string over a socket.
* `receiveMessage()` – Reads data from a socket.
* `errNClose()` – Prints an error, closes file descriptors, and exits.
* `closeFD()` – Closes one or more file descriptors.

Shared constants:

```c
#define PORT 5000
#define BUFFER_SIZE 1024
```

## How It Works

### Server

1. Creates a socket.
2. Binds to port 5000.
3. Listens for incoming connections.
4. Accepts a client.
5. Reads the client's message.
6. Sends the same message back.
7. Closes all sockets.

### Client

1. Creates a socket.
2. Connects to `127.0.0.1:5000`.
3. Sends a message.
4. Waits for the server's response.
5. Prints the echoed message.
6. Closes the socket.