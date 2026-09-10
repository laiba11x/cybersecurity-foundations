# Wireshark

Wireshark is a **network traffic analyser** used to capture and investigate network packets.

## Use Cases

* Troubleshoot network problems such as congestion.
* Detect security anomalies such as rogue hosts and unusual port usage.
* Investigate network protocols, response codes and packet data.

### Important

Wireshark is **not an IDS**. It helps analysts investigate packets, but identifying attacks depends on the analyst's knowledge.

## Main GUI Sections

* **Toolbar** – tools for filtering, sorting, exporting and processing packets.
* **Display Filter Bar** – used to filter packets.
* **Recent Files** – recently opened capture files.
* **Capture Filters & Interfaces** – choose what traffic to capture and which network interface to use.
* **Status Bar** – shows packet and tool information.

## Packet Panes

When a PCAP file is opened, Wireshark displays:

* **Packet List Pane** – summary of each packet.
* **Packet Details Panel** – detailed information about the selected packet.
* **Packet Bytes Pane** – hexadecimal and ASCII representation of the packet.

## Traffic Capture

* 🦈 **Blue shark button** → start capturing.
* 🛑 **Red button** → stop capturing.
* 🟢 **Green button** → restart capturing.

## PCAP Files

Wireshark can:

* Open and analyse PCAP/PCAPNG files.
* Merge multiple capture files.
* View capture details such as file hash, capture time, interfaces and statistics.

### Key idea

**Wireshark lets you capture and investigate network packets in detail.**

## Packet Dissection

Packet dissection means examining a packet by decoding its protocols and fields to understand what is inside it.

Wireshark breaks packets down into different sections based on the **OSI model**.

### Packet Details

When I select a packet in Wireshark, the **Packet Details pane** shows information about its different layers. Selecting a detail also highlights the corresponding bytes in the **Packet Bytes pane**.

A packet can contain several layers:

* **Frame** – basic packet/frame information.
* **Source [MAC]** – source and destination MAC addresses (Data Link layer).
* **Source [IP]** – source and destination IP addresses (Network layer).
* **Protocol** – transport protocol such as TCP or UDP, including source and destination ports.
* **Protocol Errors** – information about TCP segments that needed reassembly.
* **Application Protocol** – application protocols such as HTTP, FTP or SMB.
* **Application Data** – data specific to the application protocol.

### Key idea

Wireshark lets me **dissect a packet layer by layer**, making it easier to understand how the packet travelled through the network and what data it contains.

## Packet Investigation Tools

### Packet Numbers

Wireshark gives every packet a unique number. This makes it easier to count packets and return to a specific packet during an investigation.

### Go to Packet

I can use **Go → Go to Packet** to jump directly to a specific packet number.

### Find Packets

I can use **Edit → Find Packet** to search packet contents.

Wireshark supports:

* Display filter
* Hex
* String
* Regex

I also need to choose where to search:

* Packet list
* Packet details
* Packet bytes

The search must be performed in the correct pane because information shown in one pane may not appear in another.

### Mark Packets

Packets can be marked so I can easily identify important packets during an investigation.

Marked packets appear **black** in Wireshark.

Packet markings are temporary and are lost when the capture file is closed.

### Packet Comments

I can add comments to packets to record useful information or highlight suspicious activity.

Unlike packet markings, packet comments can be saved inside the capture file.

### Export Packets

I can export selected packets from a capture file when I need to investigate or share a specific part of the traffic.

### Export Objects

Wireshark can extract files transferred through network traffic.

Export Objects is available for protocols such as:

* HTTP
* SMB
* TFTP
* IMF
* DICOM

### Time Display Format

Wireshark can display packet timestamps in different formats.

The default is **Seconds Since Beginning of Capture**. I can change this through:

**View → Time Display Format**

UTC time can be useful when investigating events across different systems or locations.

### Expert Information

Wireshark's **Expert Information** highlights possible protocol problems or unusual events.

Severity levels include:

* **Chat** – normal protocol information
* **Note** – notable events
* **Warn** – possible problems or unusual behaviour
* **Error** – serious problems such as malformed packets

I can view Expert Information through:

**Analyse → Expert Information**

### Key idea

Wireshark provides tools to **find, mark, comment on, export and investigate packets**, making large packet captures easier to analyse.

## Packet Filtering

Wireshark has filtering tools that help me reduce network traffic and focus on packets relevant to an investigation.

### Capture vs Display Filters

* **Capture filters** – control which packets are captured.
* **Display filters** – control which packets are shown from an existing capture.

### Apply as Filter

I can right-click a packet field and choose **Apply as Filter** to show packets containing that specific value.

The status bar shows the total number of packets and how many are currently displayed.

### Conversation Filter

A **Conversation Filter** shows packets belonging to a specific conversation, such as traffic between particular IP addresses and ports.

### Colourise Conversation

**Colourise Conversation** highlights packets belonging to the same conversation without hiding other packets.

### Prepare as Filter

**Prepare as Filter** creates a display-filter query but does not apply it immediately. I can then add other conditions using **and/or** before applying it.

### Apply as Column

**Apply as Column** adds a selected packet field as a new column in the packet list. This makes it easier to compare that value across many packets.

### Follow Stream

**Follow Stream** reconstructs a network conversation so I can view the application-level data together.

For unencrypted traffic, this can reveal information such as usernames, passwords and other transferred data.

Wireshark can follow:

* TCP streams
* UDP streams
* HTTP streams

Following a stream automatically creates a display filter for that conversation.

To remove the filter, click the **X** on the display filter bar.

### Basic Display Filters

**Filter by protocol:**

```text
http
arp
dhcp
ftp
smtp
pop
imap
```

**Filter by TCP/UDP port:**

```text
tcp.port == 80
udp.port == 53
```

**Filter by IP address:**

```text
ip.addr == 192.168.1.2
```

### Key idea

Display filters help me **reduce noise and focus on relevant network traffic** during packet analysis.

