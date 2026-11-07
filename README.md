# AeroGuard Antivirus & Real-Time Protection (v1.10.7-A)

![Version](https://img.shields.io/badge/version-v1.10.7--A-blue)
![Platform](https://img.shields.io/badge/platform-Windows%2010%20|%2011-0078D6)
![License](https://img.shields.io/badge/license-Proprietary-red)
![Build](https://img.shields.io/badge/build-passing-brightgreen)
![Size](https://img.shields.io/badge/package-~14%20MB-blue)

AeroGuard is a proprietary, lightweight, and layered antivirus solution specifically designed for Windows environments. It combines deep static file inspection, rule-based heuristics, and asynchronous real-time file monitoring to detect and isolate malicious code before it executes.

It features deep scanning of NTFS ADS streams and ZIP archives without extraction, a quarantine vault, tray background execution, and Cloudflare Workers plan management.

## Table of Contents

- [Core Features & Detection Layers](#core-features--detection-layers)
- [Graphical User Interface ("Aurora")](#graphical-user-interface-aurora)
- [Getting Started](#getting-started)
- [Prerequisites](#prerequisites)
- [Installation & Launch](#installation--launch)
- [Command-Line Arguments](#command-line-arguments)
- [Technical Blueprint](#technical-blueprint)
- [Security & Privacy](#security--privacy)
- [License & Restrictions](#license--restrictions)

## Core Features & Detection Layers

AeroGuard operates on a multi-layered security model to ensure high detection accuracy while maintaining a minimal system footprint:

- **SHA-256 Signature Matching** — Fast on-disk cryptographic hash identification utilizing a Bloom pre-filter to instantly block known malware definitions (supporting local databases and up to 250,000 MalwareBazaar critical signatures).
- **Advanced PE Diagnostics** — Deep inspection of Portable Executable (PE) headers, entry points, sections, and structural integrity.
- **Heuristic Behavior Analysis** — Identifies active injection APIs, credential dumping markers, ransomware indicators, and hidden window manipulations.
- **Script & Shell Analysis** — Scans and scores PowerShell (`-EncodedCommand`, AmsiUtils, policy bypasses), Batch, VBScript, JavaScript, and HTA files.
- **Deep Code Inspection** — Evaluates section entropy (to flag packed or encrypted obfuscated binaries) and scans for OLE/Office macro automations.
- **Advanced Coverage (Deep Mode)** — Scans inside raw NTFS Alternate Data Streams (ADS) and evaluates contents inside compressed archives (`.zip`, `.jar`, Office Open XML) within strict performance and memory budgets.

## Graphical User Interface ("Aurora")

AeroGuard features a modern, fluid, hardware-accelerated user interface designed for immediate clarity and technical control:

- **Interactive Ring Gauge** — Visually displays the protection engine's state, scan progression, and threat severity.
- **Scan Console** — Easy navigation between Quick Scan (system targets, downloads, startup entries), Folder Scan, and administrative Deep Scan.
- **Quarantine Vault** — Safely isolates flagged binaries with full technical breakdowns detailing why the file was marked, its risk score, and origin. Allows secure deletion or granular file restoration.
- **Activity & Feed Logs** — Displays live event logs from the underlying security engine in chronological order.

## Getting Started

### Prerequisites

- **Operating System:** Windows 10 / Windows 11 (Architecture independent)
- **Environment:** PowerShell 5.1+ with WinForms capabilities

### Installation & Launch

1. Download the complete package or clone the repository.
2. Run the master script file (`AeroGuard.bat`).
3. (Optional) Run with administrative privileges to unlock the Deep Scan features and NTFS alternate stream inspection.

### Command-Line Arguments

```powershell
# Launch AeroGuard minimized directly to the system tray
AeroGuard.bat --background

# Force launch directly into administrative Deep Scan mode
AeroGuard.bat --deep-scan
```

## Technical Blueprint

```
┌────────────────────────────────┐
│   AeroGuard.bat (Bootstrap)    │
└───────────────┬────────────────┘
                │ (Compiles/Loads)
                ▼
┌────────────────────────────────┐
│   AeroGuardEngine.dll / C#     │
└───────────────┬────────────────┘
                │
┌───────────────┼───────────────┐
▼               ▼               ▼
┌───────────────┐┌───────────────┐┌───────────────┐
│   Signature   ││   Static PE   ││  Heuristic    │
│   Matching    ││   Analysis    ││  Scanners    │
│(Bloom/SHA-256)││(Entropy/APIs) ││(Macros/Shell) │
└───────────────┘└───────────────┘└───────────────┘
```

## Security & Privacy

- **100% Local Processing:** File paths, binary hashes, script contents, or document names never leave your local machine.
- **Cloud Connectivity Transparency:** The optional cloud reporting features only transmit basic diagnostic data (installation ID, generic device name, app version, public IP reflection, and last-seen time) to the Control Panel for license/plan synchronization purposes.

## License & Restrictions

Copyright (c) 2026 Fifko_Hraje. All rights reserved.

AeroGuard is proprietary software. No permission is granted to copy, modify, publish, redistribute, sublicense, or create derivative works except under a separate explicit written license from the copyright holder. Reverse engineering, decompilation, and disassembly are prohibited to the extent permitted by applicable law.
