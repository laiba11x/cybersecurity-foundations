## Packets and Frames

Data is split into small pieces when travelling across a network.

* **Packet:** Layer 3 (Network Layer) — contains information such as **IP addresses**.
* **Frame:** Layer 2 (Data Link Layer) — contains the packet and adds information such as **MAC addresses**.

### Encapsulation

**Encapsulation** is the process of adding information to data as it moves down the OSI layers.

A simple way to remember it:

**Frame → contains the Packet → contains the data**

### Common Packet Headers

* **TTL (Time to Live):** prevents packets from travelling around a network forever.
* **Checksum:** helps check whether data has been corrupted or changed.
* **Source Address:** IP address of the device sending the packet.
* **Destination Address:** IP address of the device receiving the packet.

### Key Takeaway

**Packet = Layer 3 + IP addresses**
**Frame = Layer 2 + MAC addresses**

## TCP/IP

**TCP (Transmission Control Protocol)** is a connection-based protocol that provides reliable data transmission.

### TCP/IP Model

The TCP/IP model has **4 layers**:

1. **Application**
2. **Transport**
3. **Internet**
4. **Network Interface**

Data is **encapsulated** as it moves through the layers. **Decapsulation** is the reverse process.

### TCP Headers

TCP packets contain information such as:

* **Source Port:** port used by the sender.
* **Destination Port:** port used by the receiving application/service.
* **Source IP:** sender's IP address.
* **Destination IP:** receiver's IP address.
* **Sequence Number:** helps keep data in the correct order.
* **Acknowledgement Number:** confirms received data.
* **Checksum:** checks data integrity.
* **Flags:** control how the connection is handled.
* **Data:** the actual information being transmitted.

## TCP Three-Way Handshake

TCP must establish a connection before sending data.

The **three-way handshake** is:

1. **SYN** — client requests a connection.
2. **SYN/ACK** — server acknowledges the request and responds.
3. **ACK** — client acknowledges the server.

Once the connection is established, **data can be sent**.

### Other TCP Messages

* **FIN:** properly closes a TCP connection.
* **RST:** abruptly terminates a connection when there is a problem.

### Sequence Numbers

TCP uses **sequence numbers** to keep data in the correct order and ensure that data is received correctly.

### Key Takeaway

**TCP = connection-based and reliable.**

**Three-way handshake = SYN → SYN/ACK → ACK**

**FIN = close connection**
**RST = abruptly terminate connection**

## UDP (User Datagram Protocol)

**UDP** is a protocol used to send data between devices.

Unlike TCP, UDP is **stateless**, meaning it does not establish a connection before sending data.

* No three-way handshake.
* No acknowledgement that data was received.
* No guarantee that packets arrive.
* Faster than TCP because less processing is required.
* Useful when speed is more important than perfect reliability.

### UDP Headers

UDP packets contain information such as:

* **Source IP:** IP address of the sender.
* **Destination IP:** IP address of the receiver.
* **Source Port:** port used by the sender.
* **Destination Port:** port used by the receiving application.
* **TTL:** prevents packets from travelling forever.
* **Data:** the information being transmitted.

### Common Uses

UDP can be useful for:

* Video streaming
* Voice/video calls
* Situations where some data loss is acceptable

### Key Takeaway

**UDP = fast, connectionless and does not guarantee delivery.**

**TCP = reliable and connection-based.**

## Ports

A **port** is a numerical endpoint used by applications to send and receive network data.

Ports range from **0–65,535**.

Applications commonly use standard ports so devices know which service they are communicating with.

### Common Ports

| Protocol | Port | Purpose                          |
| -------- | ---: | -------------------------------- |
| FTP      |   21 | File transfer                    |
| SSH      |   22 | Secure remote login (text-based) |
| HTTP     |   80 | Web traffic                      |
| HTTPS    |  443 | Secure web traffic               |
| SMB      |  445 | File and device sharing          |
| RDP      | 3389 | Remote desktop                   |

Ports **0–1024** are known as common ports.

A service can use a different port from its standard one. For example, a web server could run on **8080** instead of 80. In this case, the port can be specified using a colon:

`IP:Port`

### Key Takeaway

**Ports identify where network services communicate.**

Different protocols commonly use different ports, such as **HTTP → 80**, **HTTPS → 443**, and **SSH → 22**.
