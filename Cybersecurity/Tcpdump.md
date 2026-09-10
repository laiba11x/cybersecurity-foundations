# Tcpdump

**tcpdump** is a command-line tool used to capture and inspect network traffic.

### Network Interface

Use `-i` to choose which network interface to capture from.

```bash
tcpdump -i ens5
```

To capture from all interfaces:

```bash
tcpdump -i any
```

I can use `ip a s` to see available network interfaces.

### Save Captured Packets

Use `-w` to save captured packets to a file.

```bash
tcpdump -i ens5 -w capture.pcap
```

The capture can then be opened later in Wireshark.

### Read a Capture File

Use `-r` to read packets from an existing capture file.

```bash
tcpdump -r capture.pcap
```

### Limit Captured Packets

Use `-c` to specify how many packets to capture.

```bash
tcpdump -i ens5 -c 5
```

Without `-c`, tcpdump continues capturing until I stop it with **Ctrl+C**.

### Disable Name Resolution

By default, tcpdump may resolve IP addresses and ports into names.

* `-n` → don't resolve IP addresses
* `-nn` → don't resolve IP addresses or port numbers

Example:

```bash
tcpdump -i ens5 -c 5 -nn
```

### Verbose Output

Use `-v` to display more packet information.

```text
-v   → more verbose
-vv  → even more verbose
-vvv → maximum verbosity
```

### Useful Options

| Option | Purpose                                    |
| ------ | ------------------------------------------ |
| `-i`   | Choose network interface                   |
| `-w`   | Write packets to a file                    |
| `-r`   | Read packets from a file                   |
| `-c`   | Capture a specific number of packets       |
| `-n`   | Don't resolve IP addresses                 |
| `-nn`  | Don't resolve IP addresses or port numbers |
| `-v`   | Verbose output                             |

### Examples

```bash
tcpdump -i eth0 -c 50 -v
```

Captures 50 packets on `eth0` with verbose output.

```bash
tcpdump -i wlo1 -w data.pcap
```

Captures Wi-Fi traffic and saves it to `data.pcap`.

```bash
tcpdump -i any -nn
```

Captures traffic from all interfaces without resolving addresses or port numbers.

### Key idea

**tcpdump = command-line packet capture and analysis.**

I can capture traffic, save it to a `.pcap` file, read existing captures, limit the number of packets and control how much information is displayed.

## Basic Filtering

tcpdump filters traffic so I can focus on specific packets instead of analysing everything captured.

### Filter by Host

Capture traffic to or from a specific host:

```bash
tcpdump host example.com
```

Source host only:

```bash
tcpdump src host 192.168.1.10
```

Destination host only:

```bash
tcpdump dst host 192.168.1.10
```

### Filter by Port

Capture traffic using a specific port:

```bash
tcpdump port 53
```

Source port:

```bash
tcpdump src port 53
```

Destination port:

```bash
tcpdump dst port 53
```

### Filter by Protocol

I can filter traffic by protocol:

```bash
tcpdump tcp
tcpdump udp
tcpdump icmp
tcpdump ip
tcpdump ip6
```

For example:

```bash
sudo tcpdump -i ens5 icmp -n
```

captures ICMP traffic.

### Logical Operators

I can combine filters using:

* **and** – both conditions must be true.
* **or** – either condition can be true.
* **not** – excludes a condition.

Examples:

```bash
tcpdump host 1.1.1.1 and tcp
```

```bash
tcpdump udp or icmp
```

```bash
tcpdump not tcp
```

### Read and Filter a Capture File

I can use `-r` to read an existing capture and apply a filter:

```bash
tcpdump -r traffic.pcap src host 192.168.124.1 -n
```

I can pipe the output to `wc` to count the results:

```bash
tcpdump -r traffic.pcap src host 192.168.124.1 -n | wc
```

### Useful Filtering Commands

| Command                | Purpose                    |
| ---------------------- | -------------------------- |
| `host IP`              | Filter by host             |
| `src host IP`          | Filter by source host      |
| `dst host IP`          | Filter by destination host |
| `port PORT`            | Filter by port             |
| `src port PORT`        | Filter by source port      |
| `dst port PORT`        | Filter by destination port |
| `tcp` / `udp` / `icmp` | Filter by protocol         |
| `and`                  | Both conditions            |
| `or`                   | Either condition           |
| `not`                  | Exclude a condition        |

### Key idea

**tcpdump filtering reduces network noise so I can focus on the traffic relevant to my investigation.**

## Advanced Filtering

Tcpdump can filter packets using more specific conditions, which is useful when analysing large packet captures.

### Packet Length

* `greater LENGTH` → packets greater than or equal to the specified length
* `less LENGTH` → packets less than or equal to the specified length

Example:

```bash
tcpdump -r traffic.pcap "greater 1000"
```

### Binary Operations

Binary operations work with bits (0 and 1):

* `&` = AND → returns 1 only when both bits are 1
* `|` = OR → returns 1 when at least one bit is 1
* `!` = NOT → inverts the bit

### Header Bytes

Tcpdump can inspect specific bytes in protocol headers using:

```text
proto[expr:size]
```

* `proto` → protocol, such as `tcp`, `ip`, `udp`, `ether`
* `expr` → byte offset, where `0` is the first byte
* `size` → number of bytes to inspect (1 by default)

### TCP Flags

TCP flags can be used to filter specific types of TCP packets.

Common flags:

* `tcp-syn` → SYN
* `tcp-ack` → ACK
* `tcp-fin` → FIN
* `tcp-rst` → RST
* `tcp-push` → PUSH

Examples:

```bash
tcpdump "tcp[tcpflags] == tcp-syn"
```

Shows TCP packets with **only the SYN flag** set.

```bash
tcpdump "tcp[tcpflags] & tcp-syn != 0"
```

Shows TCP packets with the **SYN flag set**, even if other flags are also set.

```bash
tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"
```

Shows TCP packets with **SYN or ACK** set.

### Key Takeaway

Advanced tcpdump filters allow me to narrow down packet captures very precisely, including by **packet size, header contents, and TCP flags**.

## Output Options

Tcpdump has several options that change how packet information is displayed.

* `-q` → **Quick output** — shows brief packet information.
* `-e` → **Link-level header** — shows MAC addresses and Ethernet information.
* `-A` → **ASCII** — displays packet data as readable ASCII text.
* `-xx` → **Hexadecimal** — displays packet data in hexadecimal format.
* `-X` → **Hex + ASCII** — displays packet data in both hexadecimal and ASCII.

### Examples

```bash
tcpdump -r traffic.pcap -q
tcpdump -r traffic.pcap -e
tcpdump -r traffic.pcap -A
tcpdump -r traffic.pcap -xx
tcpdump -r traffic.pcap -X
```

### Quick Memory Trick

`-q` = Quick
`-e` = Ethernet/MAC
`-A` = ASCII
`-xx` = Hex
`-X` = Hex + ASCII
