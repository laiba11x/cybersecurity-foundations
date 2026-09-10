# ARP — Address Resolution Protocol

## What is ARP?

* **ARP (Address Resolution Protocol)** finds the **MAC address** associated with an IP address on the same Ethernet/WiFi network.
* A device needs the destination MAC address to create the **Layer 2 data-link frame**.
* MAC addresses are **48-bit** addresses usually written in hexadecimal, e.g. `7C:DF:A1:D3:8C:5C`.

## How ARP Works

Suppose a device knows:

* Target IP: `192.168.66.1`
* But does not know the target's MAC address.

It sends an **ARP Request** asking:

> Who has this IP address?

The request is sent to the **broadcast MAC address**:

`ff:ff:ff:ff:ff:ff`

The device that owns the IP address responds with an **ARP Reply** containing its MAC address.

After this, the two devices can communicate using Layer 2 frames.

### ARP Request → ARP Reply

**Request:** "Who has 192.168.66.1?"

**Reply:** "192.168.66.1 is at [MAC address]"

## Important

* ARP translates **IP address → MAC address**.
* ARP is used when communicating with another device on the **same local network**.
* An ARP Request/Reply is **not carried inside UDP or TCP**.
* ARP is carried directly inside an **Ethernet frame**.
* ARP is sometimes described as Layer 2 or Layer 3, but the important concept is that it connects **Layer 3 IP addressing with Layer 2 MAC addressing**.

### Key idea

**IP address = identifies the host**

**MAC address = identifies the network interface on the local network**

**ARP = finds the MAC address when you know the IP address**
