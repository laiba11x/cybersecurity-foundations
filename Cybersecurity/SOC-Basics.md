# SOC – Basics

## What is a SOC?

**SOC** stands for **Security Operations Centre**.

A SOC is a dedicated facility where a specialised security team continuously monitors an organisation's systems, networks, and resources for suspicious activity.

The main goal is to:

* Monitor security activity
* Detect suspicious or malicious behaviour
* Respond to security incidents
* Help prevent or reduce damage

## Why is a SOC Important?

Organisations store large amounts of confidential information in their networks and systems.

Threat actors constantly discover and exploit vulnerabilities, so traditional security practices may not be enough on their own.

A SOC provides continuous security monitoring and helps organisations respond to threats.

## SOC Monitoring

SOC teams typically operate **24 hours a day, 7 days a week (24/7)** so that suspicious activity can be detected and investigated at any time.

## Simple SOC Flow

```text
Monitor systems and networks
          ↓
Detect suspicious activity
          ↓
Investigate the activity
          ↓
Respond to the incident
          ↓
Prevent or reduce damage
```

## Key Point

> **SOC = Security Operations Centre**

> A SOC continuously monitors an organisation's systems and network to **detect, investigate, and respond to security threats**.

# SOC – Basics

## What is a SOC?

**SOC** stands for **Security Operations Centre**.

A SOC is a dedicated facility where a specialised security team continuously monitors an organisation's systems, networks, and resources for suspicious activity.

The main goal is to:

* Monitor security activity
* Detect suspicious or malicious behaviour
* Respond to security incidents
* Help prevent or reduce damage

## SOC Monitoring

SOC teams typically operate **24 hours a day, 7 days a week (24/7)** so that suspicious activity can be detected and investigated at any time.

---

# Detection and Response

The main focus of a SOC is **Detection** and **Response**.

Security solutions can bring an organisation's network and systems together so they can be monitored from a **centralised location**.

Continuous monitoring helps the SOC detect and respond to security incidents.

## Detection

### Detect Vulnerabilities

A **vulnerability** is a weakness that an attacker can exploit to perform actions beyond their permissions.

Vulnerabilities can exist in:

* Operating systems
* Applications
* Servers
* Computers
* Other devices

For example, a SOC may identify Windows computers that need to be patched against a known vulnerability.

### Detect Unauthorised Activity

The SOC monitors for activity that is not authorised.

For example, an attacker may obtain an employee's username and password and use them to access company systems.

Clues such as **geographical location** can help identify suspicious logins.

### Detect Policy Violations

A **security policy** is a set of rules and procedures designed to protect an organisation and support compliance.

Examples of policy violations can include:

* Downloading pirated media
* Sending confidential company information insecurely

What counts as a violation depends on the organisation's policies.

### Detect Intrusions

An **intrusion** is unauthorised access to a system or network.

Examples include:

* An attacker exploiting a web application
* A user visiting a malicious website and infecting their computer

---

# Response

## Incident Response

Once an incident is detected, the SOC can support the **incident response** process.

This can include:

* Reducing the impact of the incident
* Investigating what happened
* Performing **root cause analysis**

The SOC may work alongside an incident response team to carry out these activities.

---

# Three Pillars of a SOC

A mature SOC is built around three main pillars:

1. **People**
2. **Process**
3. **Technology**

These three pillars work together.

### People

Security professionals who monitor, investigate and respond to security events.

### Process

Defined procedures and workflows for handling security events and incidents.

### Technology

Security tools and solutions used to monitor systems, detect threats and support investigations.

## Simple SOC Flow

```text
People + Process + Technology
             ↓
       Continuous monitoring
             ↓
          Detection
             ↓
           Response
             ↓
     Reduce security impact
```

## Key Point

> **SOC focus = Detect and Respond**

> The three pillars of a SOC are **People, Process and Technology**.

People in a SOC

Even with security automation, people remain important.

Security tools can generate many alerts, creating alert noise. Human analysts help determine which alerts are genuinely harmful and require a response.

SOC Roles
SOC Analyst – Level 1

Level 1 analysts are the first responders to security alerts.

Responsibilities include:

Performing basic alert triage
Deciding whether an alert may be harmful
Reporting detections through the correct channels
SOC Analyst – Level 2

Level 2 analysts investigate alerts that require deeper analysis.

Responsibilities include:

Performing deeper investigations
Correlating information from multiple sources
Conducting more detailed analysis
SOC Analyst – Level 3

Level 3 analysts are experienced security professionals who perform more advanced work.

Responsibilities include:

Proactively looking for threat indicators
Supporting incident response
Handling serious security incidents
Supporting containment, eradication and recovery
Security Engineer

Security Engineers deploy and configure the security solutions used by the SOC.

Their responsibilities include:

Deploying security tools
Configuring security solutions
Ensuring the tools operate correctly
Detection Engineer

A detection rule is logic used by security solutions to identify potentially harmful activity.

Detection Engineers create and maintain these rules.

Level 2 and Level 3 analysts may also create detection rules, depending on the organisation.

SOC Manager

The SOC Manager oversees the SOC team's processes and provides support to the team.

They also communicate with the CISO (Chief Information Security Officer) about the SOC's security posture and activities.

SOC Hierarchy
SOC Manager
     ↓
Security Engineer / Detection Engineer
     ↓
SOC Analyst Level 3
     ↓
SOC Analyst Level 2
     ↓
SOC Analyst Level 1

The exact roles and structure can vary depending on the size and criticality of the organisation.

Easy Memory

Level 1 = Triage

Level 2 = Investigate

Level 3 = Advanced investigation + incident response

Security Engineer = Deploy and configure

Detection Engineer = Build detection rules

SOC Manager = Manage the SOC

Processes in a SOC

Each SOC role follows processes to help detect, investigate and respond to security events.

Alert Triage

Alert triage is the first response to a security alert.

The analyst examines the alert to:

Understand what happened
Determine its severity
Prioritise the alert
Decide whether further investigation is required

A useful way to perform triage is by answering the 5 Ws:

5 Ws	Question
What?	What happened?
When?	When did it happen?
Where?	Where did it happen?
Who?	Who was involved?
Why?	Why did it happen?
Example

Alert: Malware detected on host GEORGE PC

What?   → A malicious file was detected.
When?   → 13:20 on 5 June 2024.
Where?  → GEORGE PC.
Who?    → User George.
Why?    → The file was downloaded from a pirated software website.

The 5 Ws help the analyst understand the alert and decide how it should be handled.

Reporting

Harmful alerts may need to be escalated to higher-level analysts.

The alert can be recorded as a ticket and assigned to the relevant person or team.

A report should normally include:

The 5 Ws
Analysis of the activity
Relevant evidence
Screenshots where appropriate
Incident Response and Forensics

Some detections may indicate highly malicious or critical activity.

In these situations, higher-level teams may begin incident response.

A detailed forensic investigation may also be required to determine the root cause.

Forensics involves analysing artifacts from a system or network to understand what happened and how the incident occurred.

SOC Process Flow
Security alert
      ↓
Alert triage
      ↓
Answer the 5 Ws
      ↓
Determine severity
      ↓
Report / escalate
      ↓
Incident response
      ↓
Forensics (when required)
      ↓
Determine root cause
Easy Memory

Alert triage = understand and prioritise the alert

5 Ws = What, When, Where, Who, Why

Reporting = document and escalate

Incident response = respond to serious incidents

Forensics = analyse evidence to find the root cause

Technology in a SOC

Technology refers to the security solutions used by the SOC for detection and response.

People and processes alone are not enough. Security solutions help reduce manual effort, centralise information and automate parts of detection and response.

An organisation may have many devices and applications across its network. Monitoring each one individually would require significant time and resources.

Security solutions can centralise information from these devices and applications.

SIEM

SIEM stands for Security Information and Event Management.

SIEM is widely used in SOC environments.

It:

Collects logs from different log sources
Correlates information from multiple sources
Uses detection rules to identify suspicious activity
Generates alerts when a rule matches

Modern SIEM solutions can also use:

User behaviour analytics
Threat intelligence
Machine learning
Important Note

SIEM provides Detection capabilities in the SOC.

EDR

EDR stands for Endpoint Detection and Response.

EDR provides detailed visibility into activity on endpoint devices.

It can provide:

Real-time visibility
Historical activity
Endpoint detection
Detailed investigation capabilities
Automated responses

EDR operates at the endpoint level.

Easy Memory

EDR = monitor, investigate and respond to endpoint activity

Firewall

A firewall is a network security control that acts as a barrier between networks, such as an internal network and the Internet.

It:

Monitors incoming and outgoing traffic
Filters unauthorised traffic
Helps identify suspicious traffic
Can block suspicious traffic
Other SOC Technologies

Other security solutions commonly used in SOC environments include:

Antivirus
EPP (Endpoint Protection Platform)
IDS/IPS
XDR
SOAR

The technologies selected by an organisation depend on factors such as its threat surface and available resources.

Easy Memory

SIEM = centralised logs + detection

EDR = endpoint visibility + detection + response

Firewall = network traffic filtering

Technology = security tools used to support SOC detection and response
