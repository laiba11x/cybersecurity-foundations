# Digital Forensics – Basics

## What is Forensics?

**Forensics** is the use of methods and procedures to investigate and solve crimes.

The branch of forensics that investigates crimes involving digital devices is called **digital forensics**.

## What is Digital Forensics?

**Digital forensics** involves collecting, preserving and analysing evidence from digital devices to investigate cyber crimes and support legal action.

### Cyber Crime

A **cyber crime** is any criminal activity carried out using or involving a digital device.

Digital devices that may contain evidence include:

* Computers and laptops
* Mobile phones
* Hard drives
* USB drives
* Other storage devices

## Digital Forensics Process

A digital forensics team may:

```text
Digital crime
     ↓
Collect evidence securely
     ↓
Preserve the evidence
     ↓
Analyse digital devices
     ↓
Find relevant evidence
     ↓
Document findings
     ↓
Support legal action
```

## Example of Digital Forensics

Law enforcement may find several digital devices during an investigation, such as:

* A laptop
* A mobile phone
* A hard drive
* A USB drive

These devices can be handed to a digital forensics team for examination.

### Examples of Evidence

Investigators may discover:

| Device       | Possible Evidence                      |
| ------------ | -------------------------------------- |
| Laptop       | Digital maps, photos, videos           |
| Hard drive   | Documents, plans, security information |
| Mobile phone | Chat groups, messages, call records    |
| USB drive    | Stored files and documents             |

For example, investigators could find:

* A **digital map** of a bank used for planning.
* A document showing **entrances and escape routes**.
* Information about the bank's **physical security controls**.
* Photos and videos of **previous robberies**.
* Chat groups and call records related to the crime.

## Key Point

> **Digital forensics = investigating digital devices to find and analyse evidence related to a crime.**

The evidence must be handled carefully so that it can be used appropriately during an investigation and, where necessary, in legal proceedings.

NIST Digital Forensics Process

The National Institute of Standards and Technology (NIST) defines a general digital forensics process consisting of four phases:

Collection
Examination
Analysis
Reporting
1. Collection

The first phase is collecting digital evidence.

Investigators identify the devices from which evidence can be collected, such as:

Computers
Laptops
Digital cameras
USB drives

The original evidence must be protected from being altered or tampered with.

Investigators should also maintain proper documentation of the evidence collected.

2. Examination

Collected evidence can contain a very large amount of data.

The examination phase involves filtering the data and extracting information that is relevant to the investigation.

For example:

Thousands of files
      ↓
Filter by date/time
      ↓
Relevant files
      ↓
Send for analysis
3. Analysis

During analysis, investigators examine and correlate different pieces of evidence to determine what happened.

The aim is to identify activities relevant to the case and establish them in chronological order.

For example:

Evidence A + Evidence B + Evidence C
              ↓
          Correlation
              ↓
      Reconstruct activity
              ↓
        Draw conclusions
4. Reporting

The final phase is reporting.

A detailed report documents:

Investigation methodology
Evidence examined
Findings
Conclusions
Recommendations, where appropriate

Reports may be presented to:

Law enforcement
Executive management
Other relevant parties

An executive summary can be included so that people without technical knowledge can understand the main findings.

Easy Memory

Collection → Examination → Analysis → Reporting

Types of Digital Forensics

Different types of digital evidence require different tools and techniques.

Computer Forensics

Computer forensics investigates computers, which are commonly involved in cyber crimes.

Evidence may include:

Files
User activity
System information
Application data
Mobile Forensics

Mobile forensics investigates mobile devices.

Evidence can include:

Call records
Text messages
GPS locations
Other mobile data
Network Forensics

Network forensics investigates activity across a network rather than just a single device.

A major source of evidence is:

Network traffic logs
Database Forensics

Database forensics investigates incidents involving databases.

This can include:

Unauthorised access
Data modification
Data exfiltration
Cloud Forensics

Cloud forensics investigates data and activity stored within cloud infrastructure.

Cloud investigations can be challenging because investigators may have limited access to some evidence within cloud environments.

Email Forensics

Email forensics investigates emails to determine whether they are associated with activities such as:

Phishing
Fraudulent campaigns
Types at a Glance
Type	Main focus
Computer forensics	Computers and their data
Mobile forensics	Mobile devices
Network forensics	Network activity and traffic
Database forensics	Database intrusion and data changes
Cloud forensics	Cloud infrastructure and data
Email forensics	Emails and email-based attacks
Key Points

NIST process: Collection → Examination → Analysis → Reporting

Collection = gather and preserve evidence

Examination = filter and extract relevant evidence

Analysis = correlate evidence and determine what happened

Reporting = document the investigation and findings

Different types of digital forensics focus on different sources of evidence.

# Evidence Acquisition

**Evidence acquisition** is the process of collecting digital evidence while keeping the original data unchanged.

## Proper Authorisation

Investigators should obtain **authorisation from the relevant authorities** before collecting digital evidence.

This is important because digital evidence can contain private and sensitive information.

## Chain of Custody

A **chain of custody** is a formal record that tracks evidence throughout an investigation.

It records details such as:

* Evidence description
* Who collected it
* Date and time of collection
* Storage location
* Who accessed it and when

This helps show that the evidence has remained **reliable and has not been tampered with**.

## Write Blockers

A **write blocker** is a forensic tool that prevents data from being written to a storage device.

It allows investigators to examine or acquire evidence without modifying the original device.

### Easy Memory

> **Authorisation** = permission
> **Chain of custody** = evidence tracking
> **Write blocker** = prevents changes

# Windows Evidence Acquisition and Analysis

Windows computers and laptops are common sources of digital forensic evidence.

During the **Collection** phase, forensic images of the Windows system can be created.

A **forensic image** is a **bit-by-bit copy** of data from a device or memory.

## Types of Forensic Images

### Disk Image

A **disk image** is a copy of the data stored on a storage device such as an **HDD or SSD**.

The data is **non-volatile**, meaning it remains after the system is restarted or powered off.

Examples of data include:

* Documents
* Photos and videos
* Internet browsing history
* Other stored files

### Memory Image

A **memory image** is a copy of the data currently stored in the system's **RAM**.

The data is **volatile**, meaning it is lost when the system is powered off or restarted.

Examples include:

* Running processes
* Open files
* Current network connections
* Other information currently held in RAM

The **memory image should normally be captured first** because restarting or shutting down the system can cause volatile evidence to be lost.

## Windows Forensics Tools

### FTK Imager

**FTK Imager** is a widely used tool for:

* Creating disk images
* Viewing and analysing disk images

It provides a graphical interface and supports different image formats.

### Autopsy

**Autopsy** is an **open-source digital forensics platform** used to analyse acquired disk images.

Features include:

* Keyword searching
* Deleted file recovery
* File metadata analysis
* Extension mismatch detection

### DumpIt

**DumpIt** is a tool used to create **memory images** from Windows systems.

It uses a command-line interface and can create memory dumps in different formats.

### Volatility

**Volatility** is an open-source tool used to analyse **memory images**.

It uses **plugins** to investigate different types of memory artifacts.

It supports operating systems including:

* Windows
* Linux
* macOS
* Android

## Easy Memory

> **Disk image = non-volatile storage**

> **Memory image = volatile RAM**

> **FTK Imager = disk imaging**

> **Autopsy = disk image analysis**

> **DumpIt = memory acquisition**

> **Volatility = memory analysis**
