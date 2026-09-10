# NAT — Network Address Translation

## What is NAT?

* **NAT (Network Address Translation)** allows multiple devices with **private IP addresses** to access the Internet using a smaller number of **public IP addresses**.
* This helps conserve the limited IPv4 address space.
* For example, 20 computers can share a single public IP address instead of each needing its own public IP.

## How NAT Works

A NAT-enabled router keeps a **translation table** that maps connections between:

* Internal/private IP address + port
* External/public IP address + port

For example:

**Inside the network:**

`192.168.0.129:15401`

**Seen by the web server:**

`212.3.4.5:19273`

The NAT router translates the private address and port into its public address and port as the connection passes through the router.

### Key idea

**Private IP + port → NAT router → Public IP + port → Internet**

NAT allows many devices on a private network to **share a public IP address**.
