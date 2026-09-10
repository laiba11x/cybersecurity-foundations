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
