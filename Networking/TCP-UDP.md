# UDP and TCP

## UDP — User Datagram Protocol

* UDP is a **transport layer (Layer 4)** protocol.
* It is **connectionless**, meaning it does not establish a connection before sending data.
* It does **not guarantee delivery** or confirm that the packet arrived.
* This makes UDP **faster**, but less reliable than TCP.
* **Port numbers** identify the specific process/application communicating on a host.
* Valid port numbers are **1–65535**. Port `0` is reserved.

**Simple example:** Sending a normal letter without delivery confirmation.

---

## TCP — Transmission Control Protocol

* TCP is a **transport layer (Layer 4)** protocol.
* It is **connection-oriented**, meaning a connection must be established before data is sent.
* TCP provides **reliable delivery**.
* It uses **sequence numbers** to detect lost or duplicated data.
* It uses **acknowledgements (ACKs)** to confirm received data.
* TCP uses port numbers to identify the communicating process.
* Valid port numbers are **1–65535**.

### TCP Three-Way Handshake

Before sending data, TCP establishes a connection using three packets:

1. **SYN** — Client asks to establish a connection.
2. **SYN-ACK** — Server responds and acknowledges the request.
3. **ACK** — Client acknowledges the server's response.

**SYN → SYN-ACK → ACK**

### UDP vs TCP

| UDP                      | TCP                        |
| ------------------------ | -------------------------- |
| Connectionless           | Connection-oriented        |
| Faster                   | More reliable              |
| No delivery confirmation | Acknowledges received data |
| No guarantee of delivery | Reliable delivery          |
| Layer 4                  | Layer 4                    |
| Uses ports               | Uses ports                 |

### Key idea

**IP address = which host/device**

**Port number = which process/application**

**UDP = fast, but no delivery guarantee**

**TCP = reliable, uses a connection and acknowledgements**
