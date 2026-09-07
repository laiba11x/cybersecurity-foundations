# Networking Basics

## What is Networking?

Networking is the connection between devices so they can communicate and share information.

A computer network can contain anything from **2 devices to billions of devices**, including:

* Computers and laptops
* Phones
* Security cameras
* Traffic lights
* Servers
* Other connected devices

Networks are used everywhere, such as for the internet, electricity systems, transport systems and collecting data.

### Why is Networking Important in Cybersecurity?

Networking is an important cybersecurity foundation because devices communicate with each other through networks. Understanding how networks work helps me understand how attacks can happen and how networks can be protected.

### Key Takeaway

**Networking = connected devices communicating and sharing information.**

## The Internet

The **Internet** is a huge network made up of many smaller networks connected together.

### Types of Networks

* **Private network** → a smaller network, such as a home, school or company network.
* **Public network** → networks that connect smaller networks together, forming the Internet.

### Internet vs World Wide Web

* **Internet** → the global network connecting devices and networks.
* **World Wide Web (WWW)** → a service that runs on the Internet and allows information and websites to be accessed and shared.

### Key Takeaway

**The Internet = many smaller networks connected together.**

Devices on a network use identifiers/labels to identify themselves. I will learn more about these next.

## Identifying Devices on a Network

Devices need ways to identify themselves and communicate with other devices.

The two main identifiers are:

* **IP address** → identifies a device on a network.
* **MAC address** → a unique identifier assigned to a device's network interface.

---

## IP Addresses

An **IP (Internet Protocol) address** identifies a device on a network.

IPv4 addresses are made up of **four octets**, for example:

```text
192.168.1.77
```

An IP address can change depending on the network a device is connected to.

### Public vs Private IP Addresses

* **Private IP address** → identifies a device within a private/local network.
* **Public IP address** → identifies a network/device to the wider Internet.

Devices on the same private network can communicate using their private IP addresses. Devices sharing a network connection can appear to the Internet through the same public IP address.

A **ISP (Internet Service Provider)** provides Internet connectivity and assigns public IP addresses.

---

## IPv4 and IPv6

### IPv4

IPv4 uses **32 bits**, giving approximately **4.29 billion possible addresses**.

Example:

```text
192.168.1.77
```

As more devices connected to the Internet, IPv4 addresses became limited.

### IPv6

IPv6 was introduced to provide a much larger number of addresses.

* Uses **128 bits**
* Supports approximately **2¹²⁸ addresses**
* Provides a much larger address space than IPv4
* Uses a different format from IPv4

---

## MAC Addresses

A **MAC (Media Access Control) address** is a unique address associated with a device's network interface.

Example:

```text
a4:c3:f0:85:ac:2d
```

MAC addresses are written using **hexadecimal** and are normally shown as six pairs separated by colons.

A MAC address is associated with the network interface and is used for communication on the local network.

---

## MAC Spoofing

**MAC spoofing** is when a device changes/fakes its MAC address to pretend to be another device.

This can be used to bypass poorly designed security controls that trust devices based only on their MAC address.

For example, if a Wi-Fi network allows a specific MAC address, another device could potentially spoof that address.

### Key Takeaways

* **IP address** → identifies a device on a network.
* **Private IP** → used within a local/private network.
* **Public IP** → used to identify a network/device to the Internet.
* **IPv4** → 32-bit addressing.
* **IPv6** → 128-bit addressing and a much larger address space.
* **MAC address** → identifier associated with a network interface.
* **MAC spoofing** → pretending to have another device's MAC address.


