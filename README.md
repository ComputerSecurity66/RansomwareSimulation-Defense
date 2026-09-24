# 🛡️ Ransomware Simulation and Defense Lab

A Windows-based cybersecurity laboratory tool designed to **simulate ransomware-related behaviors and demonstrate defensive security controls** in a controlled environment.

The project combines ransomware simulation, file integrity monitoring, quarantine, backup verification, Windows security-event monitoring, firewall containment, Controlled Folder Access, process detection, and VirusTotal threat-intelligence analysis.

> ⚠️ **EDUCATIONAL / DEFENSIVE SECURITY PROJECT**
>
> This project is intended for cybersecurity education, authorized security testing, and isolated laboratory environments.
>
> **Never run ransomware simulations against personal, business, production, or otherwise important files. Use only disposable test data inside the designated laboratory directory.**

---

## 🚀 Features

### 🛡️ Defensive Security

The application provides multiple defensive capabilities:

* Backup verification
* Automated suspicious-file quarantine
* SHA-256 file integrity baselining
* File change monitoring
* Windows firewall network containment
* Windows Security Event Log monitoring
* Controlled Folder Access configuration
* VirusTotal threat-intelligence analysis
* API key management
* Security logging

### 🧪 Ransomware Simulation

The application includes controlled simulations for:

* File-content transformation and ransomware-like `.locked` file creation
* Mass file renaming with `.ransom` extensions
* Detection of suspicious ransomware-style extensions
* Detection and termination of selected known ransomware process names

These functions are intended to demonstrate how defensive controls may respond to suspicious file activity.

---

## 📋 Main Menu

The application provides the following 13 functions:

| Option | Feature                         | Description                                                                                        |
| -----: | ------------------------------- | -------------------------------------------------------------------------------------------------- |
|      1 | Verify Backups                  | Checks backup availability, total size, and backup freshness                                       |
|      2 | Quarantine Suspicious Files     | Searches the laboratory directory for suspicious extensions and moves matching files to quarantine |
|      3 | Create File Hash Baseline       | Creates SHA-256 hashes for files in the laboratory directory                                       |
|      4 | Monitor File Changes            | Periodically compares current SHA-256 hashes against the baseline                                  |
|      5 | Block Ransomware Ports          | Creates Windows Firewall outbound blocking rules for selected ports                                |
|      6 | Monitor Privilege Escalation    | Reviews selected Windows Security Event Log entries                                                |
|      7 | Simulate File Encryption        | Simulates ransomware-style file transformation inside `C:\LabData`                                 |
|      8 | Simulate Mass File Renaming     | Renames laboratory files using a `.ransom` extension                                               |
|      9 | Detect Suspicious Extensions    | Searches for ransomware-style file extensions                                                      |
|     10 | Block Malicious Processes       | Checks for selected ransomware-related process names and can terminate matches                     |
|     11 | Enable Controlled Folder Access | Attempts to enable Microsoft Defender Controlled Folder Access                                     |
|     12 | VirusTotal Threat Analysis      | Queries VirusTotal using a file SHA-256 hash                                                       |
|     13 | API Key Management              | Set, view, clear, and test the VirusTotal API key                                                  |

---

## 🏗️ Architecture

The project is organized around several defensive security layers.

```text
                    ┌──────────────────────────────┐
                    │   RANSOMWARE DEFENSE LAB     │
                    └──────────────┬───────────────┘
                                   │
             ┌─────────────────────┼─────────────────────┐
             │                     │                     │
             ▼                     ▼                     ▼
       Recovery Layer        Detection Layer       Containment Layer
             │                     │                     │
       Backup Checks         SHA-256 Baseline       Quarantine
       Backup Freshness      File Monitoring        Firewall Rules
                             Extension Checks       Process Control
                             Security Events
                                   │
                                   ▼
                           Simulation & Testing
                                   │
                    ┌──────────────┼──────────────┐
                    │              │              │
                    ▼              ▼              ▼
             File Simulation   Mass Rename   Security Testing
                                   │
                                   ▼
                         Threat Intelligence
                                   │
                             VirusTotal API
```

---

## 📁 Laboratory Directories

The application uses dedicated Windows directories for different functions.

```text
C:\LabData
C:\Quarantine
C:\Logs
C:\Backups
```

When a `D:` drive is available, the application uses:

```text
D:\Backups
```

for the backup location.

### `C:\LabData`

This is the primary ransomware simulation and file-monitoring laboratory directory.

### `C:\Quarantine`

Suspicious files identified by the quarantine module are moved here.

### `C:\Logs`

Application activity and security-related events are written to:

```text
C:\Logs\RansomwareDefense.log
```

The file-hash baseline is stored as:

```text
C:\Logs\FileHashes.db
```

---

## 💻 Requirements

This project is designed primarily for **Windows**.

Recommended environment:

* Windows operating system
* C#/.NET development environment
* Windows PowerShell
* Microsoft Defender for Controlled Folder Access features
* Administrator privileges for firewall and Defender-related operations
* Internet connection for VirusTotal API analysis
* VirusTotal API key for Option 12

Some functions may behave differently depending on Windows security settings, permissions, Defender configuration, and available system resources.

---

## ▶️ Running the Application

Build and run the C# console application using your preferred .NET development environment.

For features that modify Windows Firewall or Microsoft Defender settings, run the application with the required administrative privileges.

After launching, the application displays the main menu:

```text
RANSOMWARE DEFENSE SYSTEM - 5 LAYER PROTECTION

DEFENSE LAYERS (Active Protection):
1. Verify Backups (Recovery Point)
2. Quarantine Suspicious Files
3. Create File Hash Baseline
4. Monitor File Changes
5. Block Ransomware Ports
6. Monitor Privilege Escalation

SIMULATION & TESTING:
7. Simulate File Encryption
8. Simulate MassFile Renaming
9. Detect Suspicious Extensions
10. Block Malicious Processes
11. Enable Controlled Folder Access
12. VirusTotal Threat Analysis

SETTINGS:
13. API Key Management
```

---

# 🧪 Recommended Laboratory Workflow

For safe testing, use disposable sample files only.

### Step 1 — Create the laboratory directory

The application can create the required directories automatically.

```text
C:\LabData
```

### Step 2 — Create a file baseline

Run:

```text
3. Create File Hash Baseline
```

The application calculates SHA-256 hashes for files in the laboratory directory.

### Step 3 — Start monitoring

Run:

```text
4. Monitor File Changes
```

The monitor periodically checks the files against their baseline hashes.

### Step 4 — Run a simulation

Run:

```text
7. Simulate File Encryption
```

or:

```text
8. Simulate MassFile Renaming
```

### Step 5 — Test detection

Run:

```text
9. Detect Suspicious Extensions
```

### Step 6 — Test quarantine

Run:

```text
2. Quarantine Suspicious Files
```

### Step 7 — Review logs

Review:

```text
C:\Logs\RansomwareDefense.log
```

This workflow demonstrates the relationship between **attack simulation, detection, containment, and logging**.

---

# 🔐 VirusTotal Integration

The project can use VirusTotal for file hash-based threat intelligence.

The workflow is:

```text
Local File
    │
    ▼
SHA-256 Calculation
    │
    ▼
VirusTotal API
    │
    ▼
Threat Analysis Result
```

The application includes API-key management for:

* Setting the API key
* Viewing API-key status
* Clearing the API key
* Testing the API connection

The key is stored using the application's Windows protection mechanism rather than being hard-coded into the source.

> **Never commit your real VirusTotal API key to GitHub.**

Use a local configuration instead.

---

# 🛡️ Defensive Components

## File Integrity Monitoring

The project creates SHA-256 baselines and compares later file hashes against those stored values.

This provides a simple file-integrity-monitoring approach for the laboratory environment.

Example:

```text
Original SHA-256
        │
        ▼
   Baseline Store
        │
        ▼
New File SHA-256
        │
        ▼
   Compare Hashes
        │
   ┌────┴────┐
   │         │
 Match    Different
   │         │
 Normal    Alert
```

---

## Automated Quarantine

The quarantine module looks for selected ransomware-style extensions, including:

```text
.locked
.ransom
.encrypted
.crypto
.virus
```

Matching files are moved into:

```text
C:\Quarantine
```

The application also records quarantine activity in its security log.

---

## Network Containment

The network-isolation module creates Windows Firewall rules for selected TCP ports, including:

```text
445   SMB
139   NetBIOS
135   RPC
3389  RDP
22    SSH
21    FTP
```

These rules are intended as a laboratory demonstration of emergency network containment.

> ⚠️ Blocking these ports can affect legitimate services and remote administration. Use this option only in an environment where the consequences are understood.

---

## Windows Security Event Monitoring

The privilege-monitoring module reviews selected Windows Security Event Log events, including:

```text
4672
4720
```

The purpose is to demonstrate how Windows security events can be examined during a defensive investigation.

---

## Controlled Folder Access

The application can attempt to enable Microsoft Defender Controlled Folder Access.

This feature requires appropriate Windows security configuration and administrative privileges.

Use caution when changing Defender settings on a real workstation.

---

# 🧪 Simulation Details

## File Encryption Simulation

The simulation operates against:

```text
C:\LabData
```

It creates `.locked` versions of files and removes the original files as part of the demonstration.

This behavior is intentionally destructive to the **test data**, which is why the feature must only be used against disposable laboratory files.

> **Important:** the current implementation is a ransomware-style simulation and does not implement real cryptographic ransomware encryption.

---

## Mass File Renaming Simulation

The application can rename laboratory files to:

```text
filename.ext.ransom
```

This demonstrates a common ransomware-style mass-renaming scenario without operating on arbitrary user directories.

---

# 📊 Security Logging

Security and application events are recorded in:

```text
C:\Logs\RansomwareDefense.log
```

Example events include:

```text
INFO
WARN
ALERT
ERROR
```

This provides an audit trail for laboratory activities.

---

# ⚠️ Known Limitations

This project is an educational defensive-security laboratory and is **not intended to replace enterprise endpoint detection and response, antivirus, backup, SIEM, or security orchestration platforms**.

Current implementation limitations include:

* File monitoring uses periodic scanning rather than a fully event-driven real-time architecture.
* The monitoring logic focuses on new and modified files and does not provide complete ransomware behavioral detection.
* Suspicious-extension detection is heuristic and does not by itself identify ransomware.
* Process protection currently relies on a predefined set of ransomware-related process names.
* Firewall containment affects legitimate network services when their ports are blocked.
* Backup verification currently focuses on backup presence, size, and freshness rather than full cryptographic backup validation.
* The current VirusTotal implementation performs hash-based lookups and depends on API availability and a valid API key.
* A file not present in the VirusTotal database should be treated as **unknown**, not as proof that the file is clean.

These limitations are intentionally documented so that the project can be evaluated realistically.

---

# 🔒 Safety

This repository contains security-testing functionality.

Use the project only:

* On systems you own or are explicitly authorized to test
* Inside an isolated cybersecurity laboratory
* With disposable test files
* With backups available before destructive simulations
* With administrator privileges only when required and understood

Do **not** run simulation functions against:

```text
C:\Users\<username>\Documents
C:\Users\<username>\Desktop
Production file servers
Business systems
Network shares
Other people's computers
```

unless you have explicit authorization and have established an appropriate test environment.

---

# 📜 Responsible Use

The author provides this project for:

* Cybersecurity education
* Defensive security research
* Malware-analysis laboratory exercises
* File-integrity monitoring demonstrations
* Windows security experimentation
* Authorized security testing

The user is responsible for ensuring that use of this project complies with applicable laws, policies, and organizational authorization requirements.

---

# 🎯 Project Goals

The main goals of this project are to demonstrate how a small Windows security tool can combine:

```text
Simulation
    ↓
Detection
    ↓
Monitoring
    ↓
Containment
    ↓
Quarantine
    ↓
Threat Intelligence
    ↓
Logging
    ↓
Recovery Awareness
```

The project is intended to provide a practical learning environment for understanding ransomware behavior and defensive security controls.

---

# 🔮 Future Improvements

Potential future development areas include:

* Event-driven file monitoring with `FileSystemWatcher`
* Deleted-file detection
* Behavioral ransomware detection
* Detection based on file-modification rate
* Entropy-based analysis
* Better process-behavior monitoring
* Firewall-rule rollback and cleanup
* Persistent structured baseline storage
* Stronger backup integrity verification
* Improved quarantine metadata
* More detailed incident-response reporting
* Windows Event Log integration improvements
* Safer simulation dry-run mode
* Dedicated laboratory-mode enforcement
* Additional threat-intelligence providers

---

# 👨‍💻 Project Status

**Status:** Active cybersecurity laboratory project

**Platform:** Windows

**Language:** C#

**Project Type:** Defensive Security / Ransomware Simulation / Cybersecurity Research

**Primary Purpose:** Education, authorized testing, and defensive security experimentation

---

# ⭐ Why This Project?

Ransomware defense is not based on a single security control.

This project demonstrates a layered approach involving:

**Backup → Integrity → Monitoring → Detection → Containment → Quarantine → Threat Intelligence → Logging**

The goal is to provide a practical Windows security laboratory rather than a single-purpose ransomware simulator.

---

# ⚠️ Disclaimer

This software is provided for educational and authorized security-testing purposes.

The author is not responsible for damage, data loss, service interruption, system modification, or other consequences resulting from misuse of the software.

**Always use disposable laboratory data when performing ransomware simulations.**
