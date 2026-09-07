## LAN Topologies

A **network topology** describes the design or layout of a network.

### Star Topology

* Devices are individually connected to a **central device**, usually a switch.
* Commonly used today because it is reliable and easy to expand.
* **Advantages:** scalable and easy to add devices.
* **Disadvantages:** more expensive because it needs more cables and networking equipment.
* If the central switch/hub fails, connected devices lose network connectivity.

### Bus Topology

* All devices connect to a single **backbone cable**.
* **Advantages:** cheap and easy to set up.
* **Disadvantages:** can become slow when lots of devices send data at once.
* The backbone cable is a **single point of failure** — if it breaks, the network can fail.

### Ring Topology

* Devices are connected directly to each other in a **loop/ring**.
* Data travels around the ring until it reaches the intended device.
* **Advantages:** less cabling and fewer bottlenecks.
* **Disadvantages:** data may need to pass through several devices before reaching its destination.
* A broken cable or device can disrupt the entire network.

## Switches

A **switch** connects multiple devices on a network, such as computers and printers.

* Devices connect to the switch using Ethernet cables.
* Switches are common in larger networks such as schools and businesses.
* A switch keeps track of which device is connected to each port.
* It forwards data to the **intended device** instead of sending it to every device.
* This makes switches more efficient than **hubs**, which send data to every port.

### Redundancy

Multiple switches or routers can be connected to provide **multiple paths** for data.

If one path fails, another path can be used, improving network reliability.

## Routers

A **router connects different networks** and passes data between them.

**Routing** is the process of finding and using a path for data to travel between networks.

### Key Difference

* **Switch:** connects devices within a network.
* **Router:** connects different networks.

* ## Subnetting

**Subnetting** is the process of splitting a larger network into smaller networks called **subnets**.

It helps organisations separate devices and departments into different parts of a network.

### Subnet Addresses

* **Network Address:** identifies the network itself.

  * Example: `192.168.1.0`
* **Host Address:** identifies a specific device on the network.

  * Example: `192.168.1.100`
* **Default Gateway:** device/address used to send data to other networks.

  * Example: `192.168.1.254`

### Subnet Mask

A **subnet mask** determines which part of an IP address represents the network and which part represents the host.

It is also made up of **32 bits** and is usually written as four numbers from `0–255`.

### Why Subnetting Is Useful

* **Efficiency:** organises network addresses.
* **Security:** separates different groups of devices.
* **Control:** allows administrators to manage different parts of a network.

**Example:** A café could use one subnet for employees and payment systems and another for public Wi-Fi.

### Key Takeaway

**Subnetting = splitting one network into smaller networks to improve organisation, security and control.**

