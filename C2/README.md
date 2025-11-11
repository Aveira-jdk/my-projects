# Cross-Platform Command & Control (C2) (Educational PoC)
**Date:** May 12, 2024  
**Type:** Solo project

**Repository:** [github.com/Aveira-jdk/Command-Control](https://github.com/Aveira-jdk/Command-Control
)
## What This Is
This is a Python client-server remote administration system for **authorized** use in lab environments.

The goal:
- Understand how remote management tools work internally.
- Practice secure communication patterns, file transfer, and session control.
- Build something testable across Windows, Linux, and macOS.

This is not malware.  
This is not for unauthorized access.  
This is an educational proof of concept.

---

## Capabilities
### 1. Remote Command Execution
The server can send shell commands to a connected client.  
The client executes them and returns stdout/stderr back to the server.

### 2. File Transfer (Upload / Download)
- Supports segmented sending/receiving of files.
- After transfer, both sides use **MD5 hash verification** to confirm integrity.

### 3. Session Management
- The server tracks active clients and lets you switch between them.
- You can open a session to a specific machine, work in it, then detach.

### 4. Client Self-Control
- The client creates a mutex/lock so it doesn't run multiple instances at once.
- If the process exits, it cleans up so it can be run again safely.

### 5. Platform Awareness
- Collects system details differently for Windows, Linux, and macOS.
- Gives basic situational awareness of the connected host.

### 6. Error Handling and Logging
- Handles disconnects, timeouts, missing files, etc.
- Uses Python's logging and structured error handling so the server doesn't just crash.

---

## Tech Stack
- **Language:** Python 3.12
- **Core modules:** `socket`, `threading`, `subprocess`, `os`, `hashlib`, `time`, `sys`, `random`, `json`, `logging`
- **Presentation on server:** `termcolor`, `prettytable` for human-readable output in the operator console

---

## Typical Flow
1. Run the server script. It starts listening on a port.
2. Run the client script on a test machine (lab/owned system).
3. Client connects back to the server using sockets.
4. From the server console you can:
   - List sessions
   - Select a session
   - Send commands
   - Upload/download files
   - View results

---

## Why This Project Exists
- Shows understanding of remote access models at the socket/protocol level.
- Demonstrates safe file movement with integrity verification.
- Shows concurrent client handling using threads.
- Shows secure operational thinking: mutex locks, cleanup, and explicit logging.

---

## Disclaimer
This tool is designed **only** for controlled environments and authorized systems.  
Any unauthorized access or deployment against machines you do not own / do not have written permission to manage is illegal and unethical.
