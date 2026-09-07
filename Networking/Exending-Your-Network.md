## Port Forwarding

**Port forwarding** allows devices on the Internet to access a service running on a device inside a private network.

For example:

* A web server has the private IP `192.168.1.10`.
* The web server runs on port `80`.
* Without port forwarding, only devices on the same local network can access it.
* With port forwarding, the router can forward traffic from a **public IP and port** to the internal server.

### Where is it configured?

Port forwarding is configured on the **network router**.

### Port Forwarding vs Firewall

* **Port forwarding:** Opens/forwards a specific port to an internal device.
* **Firewall:** Controls whether network traffic is allowed or blocked.

### Key Takeaway

**Port forwarding makes an internal service accessible from outside the local network by forwarding traffic through the router.**

## Firewalls

A **firewall** controls what network traffic is allowed to enter or leave a network.

It acts like **border security for a network**.

A firewall can make decisions based on:

* Where traffic is coming from
* Where traffic is going
* Which **port** it is using
* Which **protocol** it is using (TCP/UDP)

Firewalls perform **packet inspection** to make these decisions.

### Types of Firewalls

**Stateful firewall**

* Looks at the **entire connection**, not just individual packets.
* Can make decisions based on the connection's behaviour.
* Uses more resources.

**Stateless firewall**

* Checks individual packets against a **fixed set of rules**.
* Uses fewer resources.
* Less intelligent because it only follows its predefined rules.

### Key Takeaway

**Firewall = controls whether network traffic is allowed or blocked.**

**Stateful = looks at connections.**
**Stateless = looks at individual packets.**

## VPN (Virtual Private Network)

A **VPN** creates a secure connection (called a **tunnel**) between devices or networks over the Internet.

Devices connected through the VPN can communicate as if they are part of the same private network.

### Benefits of VPNs

* **Connects different locations:** Allows offices or networks in different places to communicate.
* **Privacy:** Encrypts traffic, helping protect data from being intercepted, especially on public Wi-Fi.
* **Anonymity:** Can hide your traffic from your ISP and other intermediaries, depending on the VPN provider's privacy practices.

### VPN Technologies

**PPP (Point-to-Point Protocol)**

* Provides authentication and encryption.
* Uses a private key and public certificate.
* Non-routable by itself.

**PPTP (Point-to-Point Tunneling Protocol)**

* Allows PPP data to travel outside the local network.
* Easy to set up and widely supported.
* Uses weaker encryption than modern alternatives.

**IPSec (Internet Protocol Security)**

* Secures and encrypts data using the IP protocol.
* Strong encryption.
* More difficult to configure.

### Key Takeaway

**VPN = secure tunnel that connects devices/networks over the Internet.**

It can provide **security, privacy and connectivity between different networks.**


## Routers

A **router** connects different networks and passes data between them.

* Operates at **Layer 3 (Network Layer)** of the OSI model.
* Uses **routing** to find the best path for data.
* Can consider factors such as:

  * Shortest path
  * Most reliable path
  * Fastest connection
* Can be configured for things such as **port forwarding** and **firewall rules**.

### Switches

A **switch** connects multiple devices within a network.

**Layer 2 switch:**

* Operates at **Layer 2 (Data Link)**.
* Uses **MAC addresses**.
* Forwards **frames** to the correct device.

**Layer 3 switch:**

* Can perform Layer 2 switching.
* Can also perform some **routing** using IP addresses.
* Operates at **Layers 2 and 3**.

### VLANs

**VLAN (Virtual Local Area Network)** allows devices on the same physical network to be separated into different virtual networks.

For example, a company could have:

* Sales VLAN
* Accounting VLAN

Both departments can access the Internet but can be prevented from communicating directly with each other.

This provides **network separation and improved security**.

### Key Takeaway

**Router → connects different networks and routes packets using IP addresses.**

**Layer 2 Switch → connects devices and forwards frames using MAC addresses.**

**Layer 3 Switch → switching + some routing.**

**VLAN → virtually separates devices into different networks.**
