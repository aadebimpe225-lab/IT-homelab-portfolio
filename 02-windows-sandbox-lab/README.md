Windows Sandbox Troubleshooting Lab
Overview
A safe, isolated testing environment built using Windows Sandbox to practice software analysis, malware risk assessment, and troubleshooting — all without any risk to the host operating system. This lab simulates the kind of cautious, methodical analysis that IT support professionals use when handling suspicious files, unknown software, or user-reported issues.
---
Skills Demonstrated
Windows Sandbox deployment and configuration
Safe file and software analysis
Malware risk assessment and triage
Troubleshooting software installations in isolated environments
Documentation of findings for a personal knowledge base
Understanding of host/guest OS isolation principles
---
What Is Windows Sandbox?
Windows Sandbox is a built-in Windows 10/11 Pro feature that creates a temporary, disposable virtual environment. Everything inside it is deleted when the sandbox closes — making it ideal for safely testing files or software that could otherwise compromise the main system.
Key properties:
Completely isolated from the host OS
Shares the host's hardware resources but not its file system (unless mapped)
Resets to a clean state every time it opens
No installation required — built into Windows
---
Lab Setup
Requirements
Windows 10/11 Pro, Enterprise, or Education
Virtualization enabled in BIOS/UEFI
Hyper-V capability (CPU must support hardware virtualization)
Enabling Windows Sandbox
```
Control Panel → Programs → Turn Windows features on or off → Windows Sandbox ✓
```
Or via PowerShell:
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName "Containers-DisposableClientVM" -All
```
---
What Was Practiced
1. Software Installation Testing
Tested the following types of software before allowing them on the host machine:
Free/open-source utilities downloaded from the internet
Browser extensions and plug-ins
System optimization tools
Portable applications from unknown publishers
Process for each test:
Download the file/installer on the host
Map the Downloads folder into the sandbox via a `wsb` config file
Run the installer inside the sandbox
Observe behavior: what processes launch, what registry keys change, any outbound connections
Document findings in the testing log
2. Suspicious File Analysis
Practiced triage of unknown email attachments and downloaded files:
Checked file extensions and actual file type (magic bytes)
Opened `.zip` files and checked for double-extension tricks (e.g., `invoice.pdf.exe`)
Ran suspicious executables and monitored behavior
Noted any signs of malicious behavior (unexpected process launches, network calls)
3. Browser Utility Testing
Safely tested browser utilities, add-ons, and configurations:
Installed browser extensions to observe permissions requested
Tested different browser settings profiles
Verified behavior of "free VPN" and "speed booster" browser extensions
---
Sample Sandbox Configuration File
Windows Sandbox can be pre-configured using `.wsb` files. Below is an example used in this lab:
```xml
<Configuration>
  <MappedFolders>
    <MappedFolder>
      <HostFolder>C:\Users\User\Downloads\SandboxTest</HostFolder>
      <SandboxFolder>C:\Users\WDAGUtilityAccount\Desktop\TestFiles</SandboxFolder>
      <ReadOnly>true</ReadOnly>
    </MappedFolder>
  </MappedFolders>
  <Networking>Disable</Networking>
  <LogonCommand>
    <Command>explorer.exe C:\Users\WDAGUtilityAccount\Desktop\TestFiles</Command>
  </LogonCommand>
</Configuration>
```
> Setting `<Networking>Disable</Networking>` prevents any potentially malicious file from making outbound connections during analysis.
---
Sample Testing Log Entry
Date	File Tested	Source	Risk Assessment	Findings	Decision
2025-01-10	`free_pdf_converter.exe`	Random website	Medium	Bundled PUP (adware installer), multiple opt-out screens	Rejected — not installed on host
2025-01-15	`notepad++_installer.exe`	notepad-plus-plus.org	Low	Clean install, no unexpected processes	Approved — installed on host
2025-01-22	`invoice_Q4.pdf.exe`	Email attachment	High	Double extension, immediately launched cmd.exe subprocess	Flagged as malicious — deleted, reported
2025-02-03	`system_optimizer_pro.exe`	Pop-up ad	High	Showed fake scan results, attempted to launch browser to payment page	Rejected — malware behavior confirmed
2025-02-18	`7zip_installer.exe`	7-zip.org	Low	Clean install, matched known hash	Approved — installed on host
---
Key Concepts Practiced
Double Extension Trick
A common social engineering technique where a file is named `document.pdf.exe` — Windows hides the `.exe` extension by default, making it appear as a PDF to the untrained eye.
Prevention: Enable "Show file name extensions" in File Explorer settings.
Process Monitoring
Used Task Manager and optionally Process Monitor (Sysinternals) inside the sandbox to observe:
What child processes a program spawns
Whether it attempts to access unexpected file paths
Network connection attempts
Hash Verification
For trusted software, compared the file's SHA-256 hash against the publisher's verified hash:
```powershell
Get-FileHash .\installer.exe -Algorithm SHA256
```
---
What I Learned
How to safely analyze unknown software without putting the host system at risk
Common signs of potentially unwanted programs (PUPs) and malware behavior
The value of isolating test environments before deploying anything to production machines
How to configure sandbox environments for specific testing scenarios
Practical judgment for when a file is safe vs. a security risk
---
Relevance to IT Support Roles
Help desk and desktop support technicians regularly receive requests involving:
"A user downloaded something and now their computer is slow"
"Is this file safe to open?"
"Can we install this free tool on company machines?"
This lab builds the mindset and methodology to answer these questions safely and professionally.
---
Lab Status
Ongoing — new software and file types tested regularly. Testing log updated with each session.
