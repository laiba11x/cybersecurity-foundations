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
