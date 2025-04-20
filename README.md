# Multi-Threaded Client-Server Chat Application (C Programming, TCP Sockets)

## Overview

This project is a **multi-threaded client-server chat application** developed in **C** for **Unix/Linux systems**.  
It allows multiple clients to connect to a central server and engage in **real-time one-on-one chat sessions**.  
The server maintains the **connection status** (`FREE`, `BUSY`) of each client and ensures smooth pairing for chats.

The project demonstrates core concepts of:
- TCP socket programming
- Multithreading
- Client-server architecture
- Real-time communication systems

---

## Features

- Handles **multiple clients** simultaneously using threads.
- **Client List** management with status (`FREE`, `BUSY`).
- Clients can **request** to chat with other available clients.
- **One-on-one** chat sessions are supported.
- **Graceful session termination** with a "goodbye" message.
- **Persistent server** that runs indefinitely.
- **Proper client disconnection** using `~quit` command.
- Server logs important events like connection, disconnection, chat start, and end.

---

## Prerequisites

- Unix/Linux operating system
- GCC compiler installed (`gcc`)
- Basic understanding of C programming, sockets, and terminal commands

---

## Project Structure

```
.
├── server.c       # Server-side code (handles multiple clients)
├── client.c       # Client-side code (connects to server, handles chat)
├── README.md      # Project documentation
```

---

## How to Run

### 1. Compile and Run the Server

Open a terminal window for the server and run:

```bash
gcc server.c -o server
./server <PORT_NUMBER>
```
Example:

```bash
./server 1235
```

The server starts listening for client connections.

---

### 2. Compile and Run the Clients

Open **separate terminal windows** for each client.

In each client terminal:

```bash
gcc client.c -o client
./client <SERVER_IP_ADDRESS> <PORT_NUMBER>
```
Example:

```bash
./client 127.0.0.1 1235
```
*(Replace `127.0.0.1` with your server's IP address if running on different machines.)*

---

## Client Commands

| Command | Description |
|:--------|:------------|
| `~list` | View list of active users and their status (FREE/BUSY) |
| `~my_id` | Display your assigned user ID |
| `~connect_to_<user_id>` | Connect to a specific user by user ID |
| `~stop` | End the current chat session |
| `~quit` | Disconnect from the server and exit |
| `<message>` | Send a message during a chat session (No spaces, max 200 characters) |

---

## Chat Session Details

- Clients must be `FREE` to initiate or accept a chat.
- Messages are sent **one at a time alternately** between two clients.
- Messages must **NOT contain spaces** and must be **less than 200 characters**.
- A **"goodbye"** message from either client **ends the chat session**.
- After ending a chat, clients return to the `FREE` status, ready for new sessions.
- The client must use `~quit` to **properly disconnect** from the server.

---

## Important Notes

- Always use `~quit` to disconnect from the server; otherwise, the server might encounter errors.
- If a client disconnects forcefully (e.g., Ctrl+C), the server may misbehave and need restarting.
- Only two clients can chat at a time. The server ensures proper matching.
- The server runs forever and logs events like user connections, disconnections, and session creations.

---

## Example Usage

```bash
Client 1> ~my_id
Your User ID: 01

Client 2> ~list
Available Users:
[01] - FREE

Client 2> ~connect_to_01
Requesting chat with User 01...

Client 1> hello_user_02_how_are_you
Client 2> I_am_good_thank_you

Client 1> goodbye
Chat session ended.
```

---

## Troubleshooting

| Issue | Solution |
|:------|:---------|
| Server crashes or hangs | Restart the server and reconnect clients |
| Client cannot connect | Check IP address, port number, and server availability |
| Server not receiving messages | Ensure clients are sending messages correctly without spaces |

---

## License

This project is intended for **academic and educational purposes only**.  
All rights reserved by the developer.

---
