# IP Addresses

An **IP address** is a unique identifier assigned to a device on a network so other devices can communicate with it.

## IPv4

* IPv4 = **Internet Protocol version 4**.
* An IPv4 address contains **32 bits**.
* It is divided into **4 octets** (bytes).
* Each octet can have a value from **0 to 255**.
* Example: `192.168.0.1`
* There are approximately **4.3 billion** possible IPv4 addresses.

### Network and Broadcast Addresses

In a typical subnet:

* The **network address** identifies the network.
* The **broadcast address** is used to communicate with all hosts on the network.

Example:

`192.168.1.0` → network address
`192.168.1.255` → broadcast address

## Subnet Mask and CIDR

A subnet mask such as:

`255.255.255.0`

can also be written as:

`/24`

`/24` means the first **24 bits** identify the network, leaving 8 bits for hosts.

For `192.168.66.0/24`:

* Network address: `192.168.66.0`
* Usable host range: `192.168.66.1 – 192.168.66.254`
* Broadcast address: `192.168.66.255`

## Finding Your IP Address

### Windows

```text
ipconfig
```

### Linux

```bash
ifconfig
ip address show
ip a s
```

## Private IP Addresses

Private IP addresses are used within private networks and are not directly routable across the public Internet.

The three RFC 1918 private ranges are:

| Range                           | CIDR         |
| ------------------------------- | ------------ |
| `10.0.0.0 – 10.255.255.255`     | `10/8`       |
| `172.16.0.0 – 172.31.255.255`   | `172.16/12`  |
| `192.168.0.0 – 192.168.255.255` | `192.168/16` |

A router can use **NAT (Network Address Translation)** to allow devices using private IP addresses to access the Internet through a public IP address.

## Routing

A **router** forwards data packets between different networks.

* Routers operate at **Layer 3 (Network layer)** of the OSI model.
* The router examines the destination IP address.
* It chooses an appropriate route to forward the packet towards its destination.
* A packet may pass through multiple routers before reaching its destination.

## How Routers Forward Packets

* A router examines the packet's **destination IP address**.
* It checks its **routing information** to decide where the packet should go next.
* The router sends the packet through the appropriate network link.
* Each router repeats this process until the packet reaches the router for the **destination network**.
* The packet is then forwarded to the destination host.
* The process is reversed when the response travels back to the original host.

**Key idea:** Routers use the **destination IP address** to determine where to forward packets.

