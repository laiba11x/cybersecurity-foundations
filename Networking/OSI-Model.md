# OSI Model

The **OSI (Open Systems Interconnection) Model** is a 7-layer framework used to understand how devices communicate over a network.

## The 7 Layers

| Layer | Name             | Main Function                                         |
| ----- | ---------------- | ----------------------------------------------------- |
| 7     | **Application**  | Provides network services to applications             |
| 6     | **Presentation** | Handles data formatting, encryption and compression   |
| 5     | **Session**      | Establishes and manages communication sessions        |
| 4     | **Transport**    | Provides reliable data delivery                       |
| 3     | **Network**      | Handles IP addressing and routing                     |
| 2     | **Data Link**    | Handles MAC addresses and local network communication |
| 1     | **Physical**     | Transmits data as bits over physical media            |

## Encapsulation

**Encapsulation** is the process where data moves down the OSI layers and each layer adds its own information.

**Sending:**

`Application → Presentation → Session → Transport → Network → Data Link → Physical`

At the receiving device, the process happens in reverse. This is called **decapsulation**.

## Layer Order

**APSTNDP**

* Application
* Presentation
* Session
* Transport
* Network
* Data Link
* Physical

## Physical Layer (Layer 1)

The **Physical Layer** is the lowest layer of the OSI model.

It deals with the **physical hardware** used to connect devices and transfer data.

Examples include:

* Ethernet cables
* Network cables
* Electrical signals
* Physical network connections

Data is transferred as **binary (1s and 0s)** using electrical or other physical signals.

### Key Takeaway

**Physical Layer = physical hardware and the signals used to transmit data.**

## Data Link Layer (Layer 2)

The **Data Link Layer** is Layer 2 of the OSI model.

It deals with **physical addressing** using **MAC addresses**.

* Receives data from the Network Layer (Layer 3).
* Adds the **destination MAC address** to help deliver the data to the correct device.
* Uses the **NIC (Network Interface Card)**, which has a MAC address.
* MAC addresses are assigned by the manufacturer and can be **spoofed**.
* Converts data into a format suitable for transmission.

### Key Takeaway

**Data Link Layer = MAC addresses and communication between devices on the same network.**

## Network Layer (Layer 3)

The **Network Layer** is Layer 3 of the OSI model.

It is responsible for **routing data between networks** using **IP addresses**.

* Determines the best path for data to travel.
* Considers factors such as distance, reliability and connection speed.
* Data is handled using **IP addresses**.
* **Routers** are Layer 3 devices because they use IP addresses to route packets.
* Protocols used for routing include **OSPF** and **RIP**.
* The Network Layer also handles **reassembling data** from smaller chunks.

### Key Takeaway

**Network Layer = IP addresses and routing data between networks.**

## Transport Layer (Layer 4)

The **Transport Layer** is Layer 4 of the OSI model. It controls how data is delivered between devices.

The two main protocols are **TCP** and **UDP**.

### TCP (Transmission Control Protocol)

TCP is designed for **reliable and accurate** data transmission.

* Establishes a connection between devices.
* Checks for errors and missing data.
* Makes sure packets are received and reassembled in the correct order.
* More reliable but **slower** than UDP.
* Used when data needs to be complete and accurate.

**Examples:** web browsing, file sharing and email.

### UDP (User Datagram Protocol)

UDP is designed for **speed** rather than reliability.

* Does not establish a continuous connection.
* Does not guarantee that packets will arrive.
* Does not perform the same error checking as TCP.
* Faster than TCP.
* Some data may be lost, but this can be acceptable for certain applications.

**Examples:** video streaming and device discovery such as DHCP.

### TCP vs UDP

| TCP                                 | UDP                                          |
| ----------------------------------- | -------------------------------------------- |
| Reliable                            | Faster                                       |
| Error checking                      | No guarantee of delivery                     |
| Packets arrive in order             | Packets may be lost/out of order             |
| Slower                              | Faster                                       |
| Used for files, web browsing, email | Used for streaming and some network services |

### Key Takeaway

**TCP = reliable and accurate.**
**UDP = fast but less reliable.**

## Session Layer (Layer 5)

The **Session Layer** is Layer 5 of the OSI model.

It is responsible for **creating, maintaining and closing connections (sessions)** between devices.

* Creates a session when a connection is established.
* Maintains the connection while data is being transferred.
* Closes the session when the connection is no longer needed or is lost.
* Uses **checkpoints** so that if data is lost, only the missing/newer data needs to be sent again.
* Each session is unique, so data travels within its specific session.

### Key Takeaway

**Session Layer = creates, manages and ends communication sessions between devices.**


## Presentation Layer (Layer 6)

The **Presentation Layer** is Layer 6 of the OSI model.

It acts as a **translator** between the application layer and the lower layers, making sure data is in a format that different systems can understand.

* Handles **data formatting and translation**.
* Helps ensure data is displayed correctly between different applications.
* Handles **data encryption and decryption**.
* **HTTPS** is an example of secure communication involving encryption at this layer.

### Key Takeaway

**Presentation Layer = translates, formats and encrypts data.**


## Application Layer (Layer 7)

The **Application Layer** is Layer 7 and is the layer closest to the user.

It contains the **protocols and rules** that applications use to communicate over a network.

* Used by applications such as web browsers, email clients and FileZilla.
* Provides ways for users and applications to interact with network data.
* Includes protocols such as **DNS (Domain Name System)**.
* **DNS** translates website domain names into IP addresses.

### Key Takeaway

**Application Layer = protocols and services that applications use to communicate over a network.**

# OSI Model

The **OSI (Open Systems Interconnection) model** is a conceptual framework that explains how communication occurs across computer networks.

It has **7 layers**, numbered from 1 at the bottom to 7 at the top.

**Mnemonic:** *Please Do Not Throw Spinach Pizza Away*

| Layer | Name         | Main Function                                             | Examples                     |
| ----- | ------------ | --------------------------------------------------------- | ---------------------------- |
| 7     | Application  | Network services for applications                         | HTTP, FTP, DNS, SMTP, IMAP   |
| 6     | Presentation | Encoding, encryption and compression                      | ASCII, Unicode, JPEG, PNG    |
| 5     | Session      | Establishes and manages sessions                          | NFS, RPC                     |
| 4     | Transport    | End-to-end communication and segmentation                 | TCP, UDP                     |
| 3     | Network      | Logical addressing and routing                            | IP, ICMP, IPSec              |
| 2     | Data Link    | Communication between devices on the same network segment | Ethernet, WiFi               |
| 1     | Physical     | Physical transmission of data                             | Cables, fibre, radio signals |

### Layer 1 — Physical

Deals with the physical medium used to transmit **0s and 1s**, such as Ethernet cables, fibre and wireless signals.

### Layer 2 — Data Link

Handles communication between devices on the **same network segment**. Uses **MAC addresses**.

### Layer 3 — Network

Handles **logical addressing and routing between different networks**. IP is a key example.

### Layer 4 — Transport

Provides **end-to-end communication** between applications. Main protocols are TCP and UDP.

### Layer 5 — Session

Establishes, maintains and synchronises communication sessions between applications.

### Layer 6 — Presentation

Handles **data encoding, compression and encryption** so applications can understand the data.

### Layer 7 — Application

Provides network services directly to applications such as web browsers. HTTP and DNS are examples.

### Key Things to Remember

* **Layer 1:** Physical
* **Layer 2:** MAC addresses
* **Layer 3:** IP addresses and routing
* **Layer 4:** TCP/UDP
* **Layer 7:** Application protocols such as HTTP and DNS

## TCP/IP Model

**TCP/IP (Transmission Control Protocol/Internet Protocol)** is an implemented networking model developed in the 1970s by the US Department of Defense.

The standard TCP/IP model has **4 layers**:

| TCP/IP Layer | Corresponding OSI Layers | Examples                    |
| ------------ | ------------------------ | --------------------------- |
| Application  | OSI 5, 6, 7              | HTTP, HTTPS, FTP, SMTP, SSH |
| Transport    | OSI 4                    | TCP, UDP                    |
| Internet     | OSI 3                    | IP, ICMP, IPSec             |
| Link         | OSI 2                    | Ethernet, WiFi              |

### Layer 1 — Link

Handles communication between devices on the same network segment.

### Layer 2 — Internet

Handles logical addressing and routing between networks. **IP** is the main example.

### Layer 3 — Transport

Provides end-to-end communication between hosts. **TCP** and **UDP** are the main protocols.

### Layer 4 — Application

Provides network services used by applications. It combines the **OSI Application, Presentation and Session layers**.

Examples include:

* HTTP / HTTPS
* FTP
* SMTP
* IMAP
* SSH
* Telnet

### OSI vs TCP/IP

The TCP/IP model combines three OSI layers:

**OSI Layers 5 + 6 + 7 → TCP/IP Application Layer**

The TCP/IP model therefore has **4 layers**, while the OSI model has **7 layers**.

> Some modern textbooks use a **5-layer TCP/IP model** by separating the Physical layer from the Link layer.

