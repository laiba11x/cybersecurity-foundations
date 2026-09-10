# VPN (Virtual Private Network)

A **VPN** creates a secure connection, called a **VPN tunnel**, between a device/network and a VPN server over the Internet.

### Why Use a VPN?

A VPN can:

* **Encrypt traffic** between the device and VPN server.
* Protect data from being easily read or modified while travelling across the Internet.
* Connect remote offices to a company's private network.
* Allow remote users to access private network resources.
* Make websites see the **VPN server's public IP address** instead of the user's usual public IP.

### How It Works

1. The device connects to a **VPN server**.
2. A secure VPN tunnel is established.
3. Traffic is encrypted and sent through the tunnel.
4. The VPN server forwards the traffic to its destination.
5. Responses return through the VPN tunnel.

### VPN and Public IP

If all Internet traffic is routed through the VPN, websites generally see the **VPN server's public IP address**.

For example, connecting to a VPN server in Japan can make websites treat the connection as coming from Japan.

### VPN Does Not Always Route All Traffic

Some VPN configurations only provide access to a private network rather than routing all Internet traffic through the VPN.

VPNs can also have **DNS or IP leaks**, so additional leak testing may be useful.

### Key idea

**VPN = an encrypted tunnel over the Internet that can securely connect devices or networks.**
