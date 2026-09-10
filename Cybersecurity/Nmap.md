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

## Host Discovery

Nmap can be used to find out which devices are **online/live** on a network.

### Specifying Targets

Nmap supports different ways of specifying targets:

* **IP range:** `192.168.0.1-10`
* **Subnet:** `192.168.0.1/24`
* **Hostname:** `example.thm`

### Ping Scan: `-sn`

The `-sn` option performs a **ping scan** to discover live hosts without scanning their services.

```bash
nmap -sn 192.168.0.0/24
```

If a host responds, Nmap reports:

```text
Host is up
```

### Local Network

On a directly connected network (Ethernet/WiFi), Nmap starts by sending **ARP requests**.

When a device responds, Nmap can also identify its:

* IP address
* MAC address
* Network card vendor

The vendor information can sometimes help identify the type of device.

### Remote Network

A remote network has one or more routers between my machine and the target.

Nmap cannot send ARP requests directly to remote hosts. Instead, it can use methods such as:

* ICMP Echo (ping)
* ICMP Timestamp requests
* TCP SYN packets
* TCP ACK packets

Nmap uses the responses to determine whether hosts are live.

### Other Host Discovery Options

Nmap provides additional discovery options:

* `-PS[portlist]` → TCP SYN discovery
* `-PA[portlist]` → TCP ACK discovery
* `-PU[portlist]` → UDP discovery

### List Scan: `-sL`

The `-sL` option **only lists the targets** that would be scanned. It does not actually scan them.

```bash
nmap -sL 192.168.0.1/24
```

This can be useful for confirming the target range before performing a scan.

### Key Takeaway

* `-sn` → discover **live hosts** without scanning their services.
* `-sL` → **list targets** without scanning them.
* Local networks → Nmap can use **ARP**.
* Remote networks → Nmap uses other discovery methods such as **ICMP and TCP**.

## Port Scanning

After discovering live hosts, Nmap can scan their ports to find **network services** that are listening for connections.

Examples of services include:

* Web servers → TCP 80/443
* DNS → UDP/TCP 53
* SSH → TCP 22

### TCP Connect Scan: `-sT`

A TCP connect scan attempts to complete the **TCP three-way handshake** with each target port.

```bash
nmap -sT TARGET
```

If the port is open, the connection is established and Nmap then closes it.

### TCP SYN Scan: `-sS`

A SYN scan only sends the first part of the TCP handshake.

```bash
nmap -sS TARGET
```

If the port is open, the target responds with **SYN-ACK**, and Nmap sends **RST** instead of completing the connection.

This can generate fewer logs than a full TCP connection and is sometimes called a **stealth scan**.

### UDP Scan: `-sU`

UDP does not use a TCP three-way handshake. Nmap can scan for services listening on UDP ports using:

```bash
nmap -sU TARGET
```

Common UDP services include:

* DNS
* DHCP
* NTP
* SNMP
* VoIP

### Choosing Which Ports to Scan

By default, Nmap scans the **1,000 most common ports**.

* `-F` → Fast mode; scans the 100 most common ports.
* `-p10-1024` → scans ports 10–1024.
* `-p-25` → scans ports 1–25.
* `-p-` → scans all ports (1–65535).
* `-p1-1023` → scans the well-known ports.

### Key Takeaway

* `-sT` → TCP connect scan
* `-sS` → TCP SYN scan
* `-sU` → UDP scan
* `-F` → 100 common ports
* `-p[range]` → choose specific ports
* `-p-` → scan all 65,535 ports

## OS Detection

The `-O` option enables **OS detection**.

```bash
nmap -sS -O TARGET
```

Nmap analyses different indicators to make an educated guess about the target's operating system.

OS detection is not always perfectly accurate.

## Service and Version Detection

The `-sV` option detects the **services and their versions** running on open ports.

```bash
nmap -sS -sV TARGET
```

For example, Nmap might identify an SSH service as OpenSSH and show its version.

## Aggressive Scan: `-A`

The `-A` option enables several advanced detection features, including:

* OS detection
* Service/version detection
* Traceroute
* Other additional detection features

```bash
nmap -A TARGET
```

## Scan Hosts That Appear Down

Sometimes a host does not respond during Nmap's host discovery phase. Nmap may therefore assume the host is down and skip the port scan.

The `-Pn` option tells Nmap to **treat the host as online** and scan it anyway.

```bash
nmap -Pn TARGET
```

## Quick Reference

| Option | Purpose                                                        |
| ------ | -------------------------------------------------------------- |
| `-O`   | OS detection                                                   |
| `-sV`  | Service and version detection                                  |
| `-A`   | OS detection, version detection, traceroute and other features |
| `-Pn`  | Scan hosts even if they appear to be down                      |

## Timing and Scan Speed

Nmap provides timing options to control how quickly scans run. Faster scans can generate more network traffic and may be more noticeable to security monitoring systems.

### Timing Templates

Nmap has six timing templates:

| Option | Name       | Speed     |
| ------ | ---------- | --------- |
| `-T0`  | Paranoid   | Slowest   |
| `-T1`  | Sneaky     | Very slow |
| `-T2`  | Polite     | Slow      |
| `-T3`  | Normal     | Default   |
| `-T4`  | Aggressive | Fast      |
| `-T5`  | Insane     | Fastest   |

Example:

```bash id="j6nq0k"
nmap -sS -T4 TARGET
```

### Parallelism

These options control how many TCP/UDP probes can be active at the same time:

```text id="p0n4sz"
--min-parallelism <numprobes>
--max-parallelism <numprobes>
```

Nmap normally adjusts the number of parallel probes automatically depending on network conditions.

### Packet Rate

These options control the number of packets sent per second:

```text id="2t3w6p"
--min-rate <number>
--max-rate <number>
```

The rate applies to the **whole scan**, not an individual host.

### Host Timeout

`--host-timeout` sets the maximum amount of time Nmap will wait for a target host.

```bash id="m4jv1c"
nmap --host-timeout 30s TARGET
```

This can be useful when scanning slow or unreliable hosts.

### Key Takeaway

* `-T0` → slowest/paranoid
* `-T3` → normal/default
* `-T4` → aggressive/faster
* `-T5` → fastest/insane
* `--min/max-parallelism` → control simultaneous probes
* `--min/max-rate` → control packets per second
* `--host-timeout` → maximum time to wait for a host

## Verbosity and Debugging

### Verbose Output

The `-v` option gives more information about what Nmap is doing during a scan.

```bash
nmap -v 192.168.1.0/24
```

Higher verbosity levels can be used:

```bash
-vv
-vvvv
-v2
-v4
```

You can also press `v` while a scan is running to increase verbosity.

### Debugging

The `-d` option provides even more detailed debugging information.

```bash
nmap -d 192.168.1.0/24
```

Debugging levels can be increased up to `-d9`.

* `-v` → verbose information
* `-vv` / `-v2` → more verbose information
* `-d` → debugging information
* `-d9` → maximum debugging detail

## Saving Scan Results

Nmap can save scan results in different formats.

| Option           | Format   | Purpose                      |
| ---------------- | -------- | ---------------------------- |
| `-oN <filename>` | Normal   | Human-readable output        |
| `-oX <filename>` | XML      | XML format                   |
| `-oG <filename>` | Grepable | Useful with `grep` and `awk` |
| `-oA <basename>` | All      | Saves all major formats      |

### Example

```bash
nmap -sS 192.168.1.1 -oA gateway
```

This creates:

```text
gateway.nmap
gateway.xml
gateway.gnmap
```

`-oA` is useful when you want to keep the scan results in multiple formats.

## Nmap Cheat Sheet

Nmap is a network scanning tool used to discover live hosts, scan ports, identify services and operating systems, control scan timing, and save scan results.

### Host Discovery

| Option | Purpose                                   |
| ------ | ----------------------------------------- |
| `-sL`  | List targets without scanning             |
| `-sn`  | Discover live hosts without port scanning |

### Port Scanning

| Option      | Purpose                                                  |
| ----------- | -------------------------------------------------------- |
| `-sT`       | TCP Connect scan – completes the TCP three-way handshake |
| `-sS`       | TCP SYN scan – sends the first step of the handshake     |
| `-sU`       | UDP scan                                                 |
| `-F`        | Fast scan – 100 most common ports                        |
| `-p[range]` | Scan a specific port/range                               |
| `-p-`       | Scan all 65,535 ports                                    |
| `-Pn`       | Treat hosts as online and scan them                      |

### Service & OS Detection

| Option | Purpose                                                         |
| ------ | --------------------------------------------------------------- |
| `-O`   | OS detection                                                    |
| `-sV`  | Service/version detection                                       |
| `-A`   | OS detection, service/version detection and additional features |

### Timing

| Option                                    | Purpose                         |
| ----------------------------------------- | ------------------------------- |
| `-T0`                                     | Paranoid – very slow            |
| `-T1`                                     | Sneaky                          |
| `-T2`                                     | Polite                          |
| `-T3`                                     | Normal/default                  |
| `-T4`                                     | Aggressive                      |
| `-T5`                                     | Insane – very fast              |
| `--min-parallelism` / `--max-parallelism` | Control parallel probes         |
| `--min-rate` / `--max-rate`               | Control packets per second      |
| `--host-timeout`                          | Maximum time to wait for a host |

### Verbosity & Debugging

| Option        | Purpose                 |
| ------------- | ----------------------- |
| `-v`          | Verbose output          |
| `-vv` / `-v4` | Higher verbosity        |
| `-d`          | Debugging output        |
| `-d9`         | Maximum debugging level |

### Saving Results

| Option           | Purpose                 |
| ---------------- | ----------------------- |
| `-oN <filename>` | Normal output           |
| `-oX <filename>` | XML output              |
| `-oG <filename>` | Grepable output         |
| `-oA <basename>` | Saves all major formats |

### Running Nmap with sudo

Running Nmap with `sudo` gives it access to features that require higher privileges, such as crafting certain packets.

For example:

```bash
sudo nmap -sS 192.168.1.1
```

Without elevated privileges, Nmap may use a TCP Connect scan (`-sT`) instead of a SYN scan (`-sS`).

### Key Takeaway

Nmap can be used to:

* Discover live hosts
* Find open ports
* Identify services and versions
* Detect operating systems
* Control scan speed
* Increase real-time scan information
* Save scan results in different formats

