# Logs – Basics

## What are Logs?

**Logs** are digital records of activities that happen on a system, application or network.

They act like **digital footprints**, recording both normal and potentially malicious activity.

Logs can help investigators determine:

* What happened
* When it happened
* Where it happened
* How it happened
* Sometimes who performed the activity

## Why are Logs Important?

Logs provide traces that can be used to investigate security incidents.

By putting information from different logs together, security teams can build a clearer picture of what happened during an attack.

```text
Activity
   ↓
Log created
   ↓
Logs collected
   ↓
Security team analyses logs
   ↓
Activity is reconstructed
   ↓
Incident investigated
```

# Uses of Logs

| Use Case                                 | Purpose                                                     |
| ---------------------------------------- | ----------------------------------------------------------- |
| **Security Events Monitoring**           | Detect unusual or suspicious activity                       |
| **Incident Investigation and Forensics** | Investigate incidents and determine what happened           |
| **Troubleshooting**                      | Find errors and help diagnose problems                      |
| **Performance Monitoring**               | Monitor application and system performance                  |
| **Auditing and Compliance**              | Maintain a record of activities for auditing and compliance |

## Security Events Monitoring

Logs can be monitored in real time to identify **anomalous behaviour**.

## Incident Investigation and Forensics

Logs provide evidence of activity during an incident.

Security teams can use them to:

* Reconstruct events
* Investigate attacks
* Perform **root cause analysis**

## Troubleshooting

Logs record errors and other system or application problems.

They can help identify and fix technical issues.

## Performance Monitoring

Logs can provide information about how applications and systems are performing.

## Auditing and Compliance

Logs create a **trail of activity**, which can help organisations meet auditing and compliance requirements.

## Key Point

> **Logs = digital footprints of activity**

Logs are useful for both **security investigations** and normal system administration.

# Log Types

Logs are divided into different categories based on the type of information they contain. This makes investigations easier because analysts can focus on the log type relevant to an incident.

| Log Type             | Main Use                                  | Examples                                                                                        |
| -------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **System Logs**      | Troubleshoot operating system issues      | System startup/shutdown, driver loading, system errors, hardware events                         |
| **Security Logs**    | Detect and investigate security incidents | Authentication, authorisation, security policy changes, user account changes, abnormal activity |
| **Application Logs** | Record application activity               | User interactions, application changes, updates, application errors                             |
| **Audit Logs**       | Track system changes and user activity    | Data access, system changes, user activity, policy enforcement                                  |
| **Network Logs**     | Monitor network traffic and connections   | Incoming/outgoing traffic, network connections, firewall logs                                   |
| **Access Logs**      | Record access to resources                | Web server, database, application and API access                                                |

### Example

To investigate **successful Windows logins**, you would look at the **Security Logs** rather than searching through every available log.

---

# Log Analysis

**Log analysis** is the process of examining logs to extract useful information and identify suspicious or unusual activity.

Large systems can generate huge numbers of log events, making it impractical to search through them manually.

Analysts therefore use **manual and automated techniques** to find relevant events.

## Basic Log Analysis Process

```text
Collect logs
     ↓
Choose the relevant log type
     ↓
Search for relevant events
     ↓
Identify unusual activity
     ↓
Investigate the findings
     ↓
Draw conclusions
```

## Easy Memory

> **System = OS**

> **Security = security activity**

> **Application = application activity**

> **Audit = changes and user activity**

> **Network = network traffic**

> **Access = resource access**

> **Log analysis = finding useful information and suspicious activity in logs**

# Windows Event Logs

Windows records many activities in **event logs**. These logs are separated into different categories.

## Main Windows Logs

### Application

Records activity related to applications, including:

* Errors
* Warnings
* Compatibility issues

### System

Records operating system activity, including:

* Driver issues
* Hardware issues
* System startup and shutdown
* Services information

### Security

The **Security log** is especially important for security investigations.

It records activities such as:

* User authentication
* User account changes
* Security policy changes
* Other security-related events

---

# Event Viewer

**Event Viewer** is a built-in Windows utility with a graphical interface for viewing and searching Windows logs.

To open it:

```text
Start → Search → Event Viewer
```

In Event Viewer:

```text
Windows Logs
    ↓
Application / System / Security
    ↓
Select a log
    ↓
View individual events
```

## Important Event Log Fields

When viewing an event, important fields include:

| Field           | Meaning                                   |
| --------------- | ----------------------------------------- |
| **Description** | Detailed information about the activity   |
| **Log Name**    | Name of the log containing the event      |
| **Logged**      | Date and time the event occurred          |
| **Event ID**    | Unique identifier for a specific activity |

---

# Important Windows Event IDs

| Event ID | Description                          |
| -------- | ------------------------------------ |
| **4624** | Successful login                     |
| **4625** | Failed login                         |
| **4634** | Successful logoff                    |
| **4720** | User account created                 |
| **4724** | Attempt to reset an account password |
| **4722** | User account enabled                 |
| **4725** | User account disabled                |
| **4726** | User account deleted                 |

You do not need to memorise every Windows Event ID, but knowing commonly used ones is useful during investigations.

### Useful One to Remember

**4624 = successful login**

**4625 = failed login**

---

# Filtering Events

Event Viewer allows you to search for specific events using **Filter Current Log**.

For example, to investigate successful logins:

```text
Filter Current Log
        ↓
Enter Event ID: 4624
        ↓
OK
        ↓
View successful login events
```

This is much faster than manually checking every event.

---

# Windows Log Investigation

During an investigation, analysts can use Event Viewer to determine what happened on a compromised system.

For example, they may investigate:

* Successful and failed logins
* Account creation or deletion
* Account changes
* Logoff activity
* The time an activity occurred
* Other suspicious events

## Investigation Flow

```text
Identify suspicious activity
          ↓
Choose relevant Windows log
          ↓
Filter by Event ID
          ↓
Examine event details
          ↓
Build a timeline of activity
          ↓
Investigate the attack
```

## Key Points

> **Event Viewer = Windows log analysis tool**

> **Security log = important for security investigations**

> **Event ID = identifies a specific activity**

> **4624 = successful login**

> **4625 = failed login**

> **Filter Current Log = quickly find relevant events**

# Web Server Access Logs

Websites record requests made by users in **access logs**.

Apache web server access logs are commonly stored at:

```text
/var/log/apache2/access.log
```

## Information in an Access Log

An access log entry can contain:

| Field           | Meaning                                            |
| --------------- | -------------------------------------------------- |
| **IP Address**  | IP address of the user making the request          |
| **Timestamp**   | Date and time of the request                       |
| **HTTP Method** | Action used for the request, such as `GET`         |
| **URL**         | Resource requested                                 |
| **Status Code** | Result returned by the server                      |
| **User-Agent**  | Information about the browser and operating system |

### Example

```text
172.16.0.1 - - [06/Jun/2024:13:58:44] "GET /products HTTP/1.1" 404 "-" "Mozilla/5.0..."
```

This tells us:

* IP = `172.16.0.1`
* Time = `06/Jun/2024:13:58:44`
* Method = `GET`
* URL = `/products`
* Status = `404`

---

# Manual Log Analysis

## `cat`

`cat` displays the contents of a text file.

```bash
cat access.log
```

It can also combine multiple log files:

```bash
cat access1.log access2.log > combined_access.log
```

## `grep`

`grep` searches a log file for a specific string or pattern.

Example:

```bash
grep "192.168.1.1" access.log
```

This displays only the lines containing that IP address.

## `less`

`less` allows you to view a large log file one page at a time.

```bash
less access.log
```

Useful controls:

| Key        | Action                 |
| ---------- | ---------------------- |
| `Space`    | Next page              |
| `b`        | Previous page          |
| `/pattern` | Search                 |
| `n`        | Next search result     |
| `N`        | Previous search result |
| `q`        | Quit                   |

## Log Rotation

Systems often **rotate logs**, creating separate files for different time periods.

For example:

```text
access.log
access1.log
access2.log
```

Multiple logs can be combined with `cat` when necessary.

---

# Practical Exercise

The provided `access.log` file is available on the AttackBox in:

```text
/root/Rooms/logs
```

Navigate there with:

```bash
cd /root/Rooms/logs
```

Then check the files:

```bash
ls
```

The goal is to use **`cat`**, **`grep`** and **`less`** to manually analyse the access log and answer the questions.

## Easy Memory

> **cat = display/combine**

> **grep = search**

> **less = view page by page**

> **Access logs = records of website requests**
