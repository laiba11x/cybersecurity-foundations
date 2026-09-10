# DHCP

## What is DHCP?

* **DHCP (Dynamic Host Configuration Protocol)** automatically configures devices when they join a network.
* It provides the network settings a device needs, including:

  * IP address and subnet mask
  * Default gateway/router
  * DNS server
* DHCP helps prevent **IP address conflicts**, where two devices accidentally use the same IP address.
* DHCP is an **application-layer protocol** that uses **UDP**.
* DHCP server → **UDP port 67**
* DHCP client → **UDP port 68**

## DORA Process

DHCP uses four main steps, known as **DORA**:

1. **Discover** — The client broadcasts a DHCPDISCOVER message looking for a DHCP server.
2. **Offer** — The DHCP server offers an available IP address and network configuration.
3. **Request** — The client sends a DHCPREQUEST message to accept the offered IP address.
4. **Acknowledge** — The server sends a DHCPACK message confirming that the IP address has been assigned.

**DORA = Discover → Offer → Request → Acknowledge**

## DHCP Broadcasts

When a device first connects, it does not have an IP address yet.

* Source IP: `0.0.0.0`
* Destination IP: `255.255.255.255`
* Destination MAC: `ff:ff:ff:ff:ff:ff`

The broadcast allows the client to find a DHCP server on the local network.

## What DHCP Provides

At the end of the DHCP process, the device receives:

* **Leased IP address** — identifies the device on the network.
* **Subnet mask** — determines the network and host portions of the IP address.
* **Gateway** — allows traffic to be routed outside the local network.
* **DNS server** — translates domain names into IP addresses.

### Key idea

**DHCP automatically gives a device the network configuration it needs to communicate.**
