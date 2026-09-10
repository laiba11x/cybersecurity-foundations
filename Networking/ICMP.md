# ICMP — Internet Control Message Protocol

## What is ICMP?

* **ICMP (Internet Control Message Protocol)** is mainly used for **network diagnostics and error reporting**.
* It operates alongside IP and is commonly used by tools such as **ping** and **traceroute/tracert**.

## Ping

* `ping` tests whether a target system is reachable.
* It uses an **ICMP Echo Request (Type 8)**.
* The target responds with an **ICMP Echo Reply (Type 0)**.
* It measures **Round-Trip Time (RTT)** — how long it takes for a packet to go to the target and for the reply to return.
* Ping can also show **packet loss**.

Example:

```bash
ping 192.168.11.1 -c 4
```

`-c 4` means send **4 packets**.

### Important

A failed ping does **not always mean the target is offline**. A firewall may block ICMP traffic.

---

## Traceroute

* `traceroute` (Linux/Unix) and `tracert` (Windows) discover the **route between your device and a target**.
* It shows the routers, or **hops**, that packets travel through.
* It uses the IP packet's **TTL (Time-to-Live)** value.
* Each router decreases the TTL by 1.
* When TTL reaches 0, the router drops the packet and sends an **ICMP Time Exceeded (Type 11)** message.
* This allows traceroute to identify the routers along the route.

Example:

```bash
traceroute example.com
```

Windows:

```cmd
tracert example.com
```

### `* * *`

If you see:

```text
5  * * *
```

it usually means that router did not respond to the traceroute probes or the response was blocked.

### Key idea

**ICMP = diagnostics and error reporting**

**ping = tests connectivity + measures RTT**

**traceroute/tracert = discovers the route/hops**

**TTL = limits how many routers a packet can pass through**
