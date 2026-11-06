
AeroGuard Antivirus & Real-Time Protection (v1.10.7-A)

AeroGuard is a proprietary, lightweight, and layered antivirus solution specifically designed for Windows environments. It combines deep static file inspection, rule-based heuristics, and asynchronous real-time file monitoring to detect and isolate malicious code before it can execute.

Core Features & Detection Layers

AeroGuard operates on a multi-layered security model to ensure high detection accuracy while maintaining a minimal system footprint:
• SHA-256 Signature Matching: Fast on-disk cryptographic hash identification utilizing a Bloom pre-filter to instantly block known malware definitions (supporting local databases and up to 250,000 MalwareBazaar critical signatures).
• Advanced PE Diagnostics: Deep inspection of Portable Executable (PE) headers, entry points, sections, and structural integrity.
• Heuristic Behavior Analysis: Identifies active injection APIs, credential dumping markers, ransomware indicators, and hidden window manipulations.
• Script & Shell Analysis: Scans and scores PowerShell (-EncodedCommand, AmsiUtils, policy bypasses), Batch, VBScript, JavaScript, and HTA files.
• Deep Code Inspection: Evaluates section entropy (to flag packed or encrypted obfuscated binaries) and scans for OLE/Office macro automations.
• Advanced Coverage (Deep Mode): Scans inside raw NTFS Alternate Data Streams (ADS) and evaluates contents inside compressed archives (.zip, .jar, Office Open XML) within strict performance and memory budgets.

Graphical User Interface ("Aurora")

AeroGuard features a modern, fluid, hardware-accelerated user interface designed for immediate clarity and technical control:
• Interactive Ring Gauge: Visually displays the protection engine's state, scan progression, and threat severity.
• Scan Console: Easy navigation between Quick Scan (system targets, downloads, startup entries), Folder Scan, and administrative Deep Scan.
• Quarantine Vault: Safely isolates flagged binaries with full technical breakdowns detailing why the file was marked, its risk score, and origin. Allows secure deletion or granular file restoration.
• Activity & Feed Logs: Displays live event logs from the underlying security engine in chronological order.

Getting Started


Prerequisites

• Operating System: Windows 10 / Windows 11 (Architecture independent)
• Environment: PowerShell 5.1+ with WinForms capabilities

Installation & Launch

AeroGuard is designed to compile its native UI helpers dynamically on boot or load its companion engine assembly directly.
1. Download the complete package or clone the repository.
2. Run the master script file (AeroGuard.bat).
3. (Optional) Run with administrative privileges to unlock the Deep Scan features and NTFS alternate stream inspection.

Command-Line Arguments
# Launch AeroGuard minimized directly to the system tray
AeroGuard.bat --background

# Force launch directly into administrative Deep Scan mode
AeroGuard.bat --deep-scan

Technical Blueprint
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
│   Matching    ││   Analysis    ││   Scanners    │
│(Bloom/SHA-256)││(Entropy/APIs) ││(Macros/Shell) │
└───────────────┘└───────────────┘└───────────────┘


Security & Privacy Commitments

• 100% Local Processing: File paths, binary hashes, script contents, or document names never leave your local machine.
• Cloud Connectivity Transparency: The optional cloud reporting features only transmit basic diagnostic data (installation ID, generic device name, app version, public IP reflection, and last-seen time) to the Control Panel for license/plan synchronization purposes.

License & Restrictions

Copyright (c) 2026 Fifko_Hraje. All rights reserved.
AeroGuard is proprietary software. No permission is granted to copy, modify, publish, redistribute, sublicense, or create derivative works except under a separate explicit written license from the copyright holder. Reverse engineering, decompilation, and disassembly are prohibited to the extent permitted by applicable law.
