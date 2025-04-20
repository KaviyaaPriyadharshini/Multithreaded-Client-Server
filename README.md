Multi-Threaded Client-Server Chat Application (TCP)
Overview
This project is a multi-threaded client-server chat application implemented in C for Unix/Linux systems using TCP sockets. It allows multiple clients to connect to a centralized server, view other connected users (with their availability status), and establish private chat sessions. Clients can communicate through the server, and all interactions, including user connections and session management, are handled reliably.

Clients can chat even from different machines on the same network.

Demo
A sample demo showing multiple clients interacting with the server and initiating chat sessions.

(Optional: You can add a GIF/screen recording link here.)

Features
Concurrent Client Connections via multi-threaded server handling

Real-Time User Status Tracking (FREE / BUSY)

User ID Management for uniquely identifying clients

Chat Matching by connecting with other free users

Graceful Chat Session Termination via "goodbye" message

Persistent Connection: Clients stay connected to the server even after ending a chat

Safe Disconnection with the ~quit command

Server Logging of user connections, chat sessions, and disconnections

Commands-Based Interface for intuitive interaction

Server runs indefinitely, handling new and returning clients

Prerequisites
Unix/Linux operating system

gcc compiler

Basic understanding of terminal operations

Networking setup (for running across different machines)

How to Run
1. Start the Server
Open a terminal and run the following commands:

bash
Copy
Edit
gcc server.c -o server
./server <PORT>
Replace <PORT> with the desired port number (e.g., 1235).

Example:

bash
Copy
Edit
./server 1235
The server will start and listen indefinitely for incoming client connections.

2. Start the Clients
Open multiple terminals (one for each client) and run the following commands in each:

bash
Copy
Edit
gcc client.c -o client
./client <SERVER-IP-ADDRESS> <PORT>
Replace:

<SERVER-IP-ADDRESS> with the IP address of the server machine (e.g., 10.10.75.20)

<PORT> with the server port number.

Example:

bash
Copy
Edit
./client 10.10.75.20 1235
Usage Instructions
Once connected, clients can use the following commands:


Command	Description
~list	List all connected users and their status (FREE/BUSY).
~connect_to_<userid>	Request to start a chat session with a user by their User ID (e.g., ~connect_to_03).
~stop	End an ongoing chat session.
~quit	Disconnect from the server and exit.
~my_id	Display your unique User ID assigned by the server.
<message>	Send a message during an active chat session (Max 200 characters, no spaces allowed).
⚡ Note: Chatting happens alternately. You can receive a message only after sending one.

Communication Protocol
All messages are routed through the server.

No direct client-to-client socket is created (centralized communication model).

Chat session ends when either client sends a goodbye message.

After ending a chat, both clients return to FREE state and can initiate new sessions.

To fully disconnect from the server, use the ~quit command.

Important Notes
Always use ~quit to disconnect. Forcefully closing the terminal without proper logout may leave dangling sessions on the server.

Message size must be < 200 characters and should not contain spaces.

If the server or client behaves unexpectedly, restart both the server and the clients.

The server is designed to run continuously, even when clients connect/disconnect multiple times.

Directory Structure
bash
Copy
Edit
.
├── server.c      # Server-side source code
├── client.c      # Client-side source code
├── README.md     # This documentation file
Future Enhancements (Optional)
Encryption of messages using SSL/TLS.

Broadcasting messages to multiple users.

GUI client implementation using GTK+ or Qt.

Authentication system (username/password).

Automatic reconnection for network failures.

Contact
For queries, suggestions, or contributions:

📩 kaviyaakpdaskc@gmail.com

License
This project is developed as an academic exercise for learning purposes.
Feel free to use and modify it.
