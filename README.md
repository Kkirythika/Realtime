Real-Time Collaborative Editing Feature:

Overview:

This project implements a **Real-Time Collaborative Editing System** that enables multiple users to edit the same document simultaneously, similar to Google Docs.
The system uses **WebSockets** to provide low-latency, real-time communication between clients and the server. All users can view updates instantly, ensuring seamless collaboration and minimizing version conflicts.

Objective:

* Enable multiple users to edit a document concurrently
* Provide real-time synchronization across all clients
* Ensure low latency (<200ms) for updates
* Maintain consistent document state

Features:

*  Real-time collaborative editing
*  Multiple users editing simultaneously
*  Instant synchronization of changes
*  WebSocket-based communication
*  Persistent storage using MySQL
*  Active users indicator
*  Automatic update broadcasting

Functional Requirements:

Editor Interface:

* Text editor for writing and editing content
* Changes reflect instantly for all users

Active Users:

* Displays currently connected users
* Each user identified by a unique name

User Interaction Flow:

1. User opens the application
2. Client connects to WebSocket server
3. Server registers the user
4. User starts typing
5. Changes are sent to server
6. Server broadcasts updates
7. All clients update instantly

Technical Stack:

Frontend:

* ReactJS
* Native WebSocket API

Backend:

* Spring Boot
* Spring WebSocket

Database:

* MySQL

Architecture:
System Architecture:

User (React UI)
      ↓
WebSocket Connection
      ↓
Spring Boot Server
      ↓
In-Memory Document State
      ↓
MySQL Database

Component Description:

* Frontend (React):** Handles UI and sends/receives updates
* WebSocket Layer:** Enables real-time communication
* Backend (Spring Boot):** Processes edits and manages users
* Memory State:** Stores latest document for fast updates
* Database (MySQL):** Stores persistent document data

WebSocket Communication:

Endpoint:
ws://localhost:9091/editor

Message Format

Client → Server

json
{
  "type": "edit",
  "user": "userA",
  "content": "Hello"
}

Server → Clients

json
{
  "type": "edit",
  "user": "userA",
  "content": "Hello"
}

Document State Management:

* Server maintains current document state
* Latest version stored in memory
* Periodically saved to database
* New users receive latest document on join

Real-Time Synchronization:

* Editor detects text changes
* Sends updates to server
* Server broadcasts updates to all users
* All clients apply updates immediately

Conflict Handling:

* Basic **last-write-wins** strategy implemented
* OT / CRDT can be used for advanced conflict resolution

Performance:

* Low latency real-time updates
* Supports multiple concurrent users
* Efficient WebSocket communication

Error Handling:

* Detects WebSocket disconnection
* Can be extended with auto-reconnect logic
* Ensures application stability

📁 Project Structure

text
Realtime-editor
│
├── backend
│   ├── config
│   ├── controller
│   ├── entity
│   ├── repository
│   ├── service    
│   ├── model
│   └── application.properties
│
├── frontend
│   ├── src
│   └── public
│
└── README.md

How to Run:

Backend:
bash
mvn clean spring-boot:run
Runs on:
http://localhost:9091

Frontend:
bash
npm install
npm start
Runs on:
http://localhost:3000

Testing:

* Open multiple browser tabs
* Type in one tab
* Changes reflect instantly in all tabs
 
Deliverables

* Full React + Spring Boot implementation
* WebSocket-based real-time system
* GitHub repository
* Documentation (README)

Acceptance Criteria:

* Multiple users can edit simultaneously
* Changes appear in real time
* Document stays consistent
* WebSocket connection remains stable

Future Improvements:

* Implement OT (Operational Transformation)
* Implement CRDT for conflict resolution
* Add cursor tracking
* Add authentication system
* Support multiple documents

Conclusion:

This project successfully implements a **real-time collaborative editing system** using WebSockets. It demonstrates efficient synchronization, multi-user support, and scalable architecture for collaborative applications.


Kiruthika Aranganathan
