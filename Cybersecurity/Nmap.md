# Nmap

## What is Nmap?

Nmap (Network Mapper) is an **open-source network scanner** used to discover devices and services on a network.

It can help me:

* Discover **live hosts** on a network.
* Find **open ports** and running services.
* Identify **service versions**.
* Perform different types of **port scans**.
* Control scan **timing and speed**.
* Save and format scan **output**.

## Discovering Live Hosts

Finding live devices manually can be slow. For example, a `/24` network contains **256 addresses**, but normally **254 are usable host addresses**.

Tools such as `ping` and `arp-scan` can help discover devices, but they have limitations:

* `ping` may fail if the target blocks ICMP traffic.
* `arp-scan` generally requires the target to be on the same local network.

Nmap provides a more flexible way to discover hosts.

## Discovering Services

After finding a live host, I can use Nmap to identify services running on it, such as:

* SSH
* Web servers
* Other network services

Manually checking thousands of ports would be very time-consuming, whereas Nmap can scan ports efficiently.

## Key Takeaway

Nmap is a flexible network-scanning tool that can be used to **discover hosts, identify open ports and services, detect service versions, and analyse networks efficiently**.
