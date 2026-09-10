# Routing and Routing Protocols

## What is Routing?

* The Internet consists of **millions of routers and billions of devices**.
* A packet may need to travel through multiple routers to reach its destination.
* Routers use **routing algorithms and routing tables** to decide which path the packet should take.
* There can be multiple possible routes between two networks.
* The router chooses an appropriate route and forwards the packet through the correct link.

## Common Routing Protocols

### OSPF — Open Shortest Path First

* Routers share information about the network topology.
* Each router can build a map of the network.
* Routers calculate efficient paths to destinations.

### EIGRP — Enhanced Interior Gateway Routing Protocol

* A **Cisco proprietary** routing protocol.
* Routers share information about reachable networks and route costs.
* Uses factors such as bandwidth and delay to choose routes.

### BGP — Border Gateway Protocol

* The **primary routing protocol used on the Internet**.
* Allows different networks, such as ISPs, to exchange routing information.
* Helps route traffic between different networks.

### RIP — Routing Information Protocol

* A simple routing protocol often used in smaller networks.
* Routers share information about reachable networks.
* Uses the **number of hops** as its main metric.
* Generally chooses the route with the fewest hops.

### Key idea

**Routing = deciding which path a packet should take to reach its destination.**

**BGP → Internet**

**OSPF → network topology / efficient paths**

**EIGRP → Cisco / route cost**

**RIP → fewest hops**
