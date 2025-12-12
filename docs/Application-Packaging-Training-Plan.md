# 🎓 Comprehensive Application Packaging Training Program
## Complete Training Curriculum:  From University Graduate to Full Application Developer

---

# Table of Contents

- [Program Overview](#program-overview)
- [Phase 1: Foundations (Weeks 1-4)](#phase-1-foundations-weeks-1-4)
  - [Week 1: Core Concepts & Windows Fundamentals](#week-1-core-concepts--windows-fundamentals)
  - [Week 2: MSI Technology Deep Dive](#week-2-msi-technology-deep-dive)
  - [Week 3: Scripting Fundamentals](#week-3-scripting-fundamentals)
  - [Week 4: Advanced Scripting and Automation](#week-4-advanced-scripting-and-automation)
- [Phase 2: SCCM/MECM Deployment (Weeks 5-8)](#phase-2-sccmmecm-deployment-weeks-5-8)
  - [Week 5: SCCM Architecture & Console Navigation](#week-5-sccm-architecture--console-navigation)
  - [Week 6: Creating SCCM Applications](#week-6-creating-sccm-applications)
  - [Week 7: SCCM Packages & Task Sequences](#week-7-sccm-packages--task-sequences)
  - [Week 8: SCCM Troubleshooting & Monitoring](#week-8-sccm-troubleshooting--monitoring)
- [Phase 3: Intune Deployment (Weeks 9-12)](#phase-3-intune-deployment-weeks-9-12)
  - [Week 9: Intune Fundamentals & Architecture](#week-9-intune-fundamentals--architecture)
  - [Week 10: Win32 App Packaging with IntuneWinAppUtil](#week-10-win32-app-packaging-with-intunewinapputil)
  - [Week 11: Deploying Win32 Apps in Intune](#week-11-deploying-win32-apps-in-intune)
  - [Week 12: Intune Troubleshooting & Advanced Features](#week-12-intune-troubleshooting--advanced-features)
- [Phase 4: Advanced Topics & Real-World Scenarios (Weeks 13-16)](#phase-4-advanced-topics--real-world-scenarios-weeks-13-16)
  - [Week 13: Advanced Packaging Techniques](#week-13-advanced-packaging-techniques)
  - [Week 14: Application Lifecycle Management](#week-14-application-lifecycle-management)
  - [Week 15: Security & Compliance](#week-15-security--compliance)
  - [Week 16: Automation, Capstone Project & Final Assessment](#week-16-automation-capstone-project--final-assessment)
- [Appendices](#appendices)
  - [Appendix A: Recommended Resources](#appendix-a-recommended-resources)
  - [Appendix B: Skills Checklist](#appendix-b-skills-checklist)
  - [Appendix C: Training Log Template](#appendix-c-training-log-template)

---

# Program Overview

## Training Summary

| Attribute | Details |
|-----------|---------|
| **Total Duration** | 16-20 weeks |
| **Daily Commitment** | 6-8 hours |
| **Target Audience** | University graduates with basic IT knowledge |
| **Prerequisites** | Basic Windows OS knowledge, fundamental IT concepts |
| **End Goal** | Independently package and deploy complex applications to SCCM and Intune |
| **Certification Path** | Microsoft Endpoint Manager certification preparation |

## Learning Methodology

| Method | Description | Time Allocation |
|--------|-------------|-----------------|
| **Theory** | Documentation, videos, reading materials | 20% |
| **Guided Practice** | Instructor-led exercises | 30% |
| **Independent Practice** | Self-directed labs | 35% |
| **Assessment** | Quizzes, practical tests, projects | 15% |

## Training Environment Requirements

| Component | Specification |
|-----------|---------------|
| **Host Machine** | Windows 10/11 Pro or Enterprise, 16GB+ RAM, 500GB+ SSD |
| **Hypervisor** | Hyper-V, VMware Workstation, or VirtualBox |
| **Virtual Machines** | Windows 10/11 Enterprise (clean images) |
| **Lab Access** | SCCM/MECM environment, Intune tenant |
| **Tools** | See Essential Tools section |

---

# Phase 1: Foundations (Weeks 1-4)

---

## Week 1: Core Concepts & Windows Fundamentals

### Day 1: Introduction to Application Packaging

#### Morning Session (4 hours): What is Application Packaging? 

##### Learning Objectives
- Define application packaging and its role in enterprise IT
- Understand the software deployment lifecycle
- Identify key stakeholders in the packaging process

##### 1.1 Definition and Purpose

**Application Packaging Definition:**
```
Application Packaging:  The process of preparing software for automated, 
silent deployment across enterprise environments with minimal user 
interaction and maximum reliability.
```

**Why Application Packaging Matters:**

| Challenge | Without Packaging | With Packaging |
|-----------|------------------|----------------|
| Consistency | Varies by technician | Identical every time |
| Time | 30-60 min per install | Seconds to minutes |
| Errors | High human error rate | Automated, tested |
| Scale | One device at a time | Thousands simultaneously |
| Audit | No documentation | Full tracking |
| Rollback | Manual uninstall | Automated removal |

##### 1.2 The Software Deployment Lifecycle

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Request   │───▶│  Packaging  │───▶│   Testing   │───▶│   Pilot     │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                                                │
┌─────────────┐    ┌─────────────┐    ┌─────────────┐           │
│  Retirement │◀───│ Maintenance │◀───│ Production  │◀──────────┘
└─────────────┘    └─────────────┘    └─────────────┘
```

**Lifecycle Phases Explained:**

| Phase | Activities | Duration | Key Outputs |
|-------|-----------|----------|-------------|
| **Request** | Receive request, gather requirements, obtain media | 1-2 days | Completed request form, installation media |
| **Packaging** | Analyze installer, create package, write scripts | 2-5 days | Deployment package, documentation |
| **Testing** | Install/uninstall testing, functionality verification | 1-3 days | Test results, bug fixes |
| **Pilot** | Deploy to limited user group, gather feedback | 3-7 days | Pilot report, adjustments |
| **Production** | Full deployment to target audience | Ongoing | Deployment reports |
| **Maintenance** | Updates, patches, troubleshooting | Ongoing | Updated packages |
| **Retirement** | Remove application, clean up | 1-2 days | Removal confirmation |

##### 1.3 Key Stakeholders

| Stakeholder | Role | Interaction |
|-------------|------|-------------|
| **Application Owner** | Requests software, defines requirements | Provides requirements, approves testing |
| **Packager** | Creates deployment package | Technical implementation |
| **Tester/QA** | Validates functionality | Reports issues |
| **Security Team** | Approves software for use | Security review |
| **Service Desk** | Supports end users | Reports issues, requests |
| **End Users** | Consumes application | Receives deployment |

#### Afternoon Session (4 hours): Types of Installers

##### 2.1 MSI (Microsoft Installer) Format

**What is an MSI? **
```
MSI files are database-driven installers that follow Microsoft's 
Windows Installer technology. They contain all files, registry 
entries, and instructions needed to install an application.
```

**MSI Characteristics:**

| Feature | Description |
|---------|-------------|
| **Structure** | Relational database with tables |
| **Extension** | .msi |
| **Technology** | Windows Installer Service |
| **Transaction-based** | Can rollback on failure |
| **Standardized** | Consistent parameters across all MSIs |
| **Patchable** | Supports . msp patch files |
| **Transformable** | Can be customized with . mst files |

**Common MSI Command-Line Parameters:**

```cmd
::  Basic Installation
msiexec /i "application.msi"

:: Silent Installation (no UI)
msiexec /i "application.msi" /qn

:: Silent with basic UI (progress bar)
msiexec /i "application.msi" /qb

:: Silent with no reboot
msiexec /i "application.msi" /qn /norestart

:: With logging
msiexec /i "application.msi" /qn /l*v "C:\Logs\install.log"

::  Uninstall by path
msiexec /x "application.msi" /qn

:: Uninstall by product code
msiexec /x {PRODUCT-CODE-GUID-HERE} /qn

:: With transform file
msiexec /i "application.msi" /qn TRANSFORMS="custom.mst"

:: With properties
msiexec /i "application.msi" /qn INSTALLDIR="C:\CustomPath" ALLUSERS=1

:: Administrative installation (extracts files)
msiexec /a "application.msi" TARGETDIR="C:\ExtractedFiles"

:: Repair installation
msiexec /f "application.msi"

::  Advertise (install on first use)
msiexec /j "application.msi"
```

**MSI UI Levels Explained:**

| Switch | UI Level | Description |
|--------|----------|-------------|
| `/qn` | None | Completely silent, no UI |
| `/qb` | Basic | Progress bar only |
| `/qr` | Reduced | Reduced UI, no wizard |
| `/qf` | Full | Full wizard UI |
| `/qn+` | None + modal | Silent with final dialog |
| `/qb+` | Basic + modal | Basic with final dialog |
| `/qb! ` | Basic no cancel | Basic UI, no cancel button |

**MSI Return Codes:**

| Code | Meaning |
|------|---------|
| 0 | Success |
| 1601 | Windows Installer service not accessible |
| 1602 | User cancelled installation |
| 1603 | Fatal error during installation |
| 1618 | Another installation is in progress |
| 1619 | Installation package could not be opened |
| 1620 | Installation package invalid |
| 1622 | Error opening installation log file |
| 1625 | Installation prohibited by policy |
| 1638 | Another version already installed |
| 1641 | Reboot initiated |
| 3010 | Reboot required |

##### 2.2 EXE (Executable) Installers

**Types of EXE Installers:**

| Installer Type | Vendor | Silent Switch | Common Characteristics |
|---------------|--------|---------------|----------------------|
| **InstallShield** | Flexera | `/s /v"/qn"` | Wraps MSI, common in enterprise |
| **Inno Setup** | Jordan Russell | `/VERYSILENT /SUPPRESSMSGBOXES` | Open source, popular |
| **NSIS** | Nullsoft | `/S` | Lightweight, open source |
| **WiX** | Microsoft | `/quiet` | Open source, MSI-based |
| **InstallAnywhere** | Flexera | `-i silent` | Cross-platform |
| **Setup Factory** | Indigo Rose | `/S` | Visual installer creator |
| **Advanced Installer** | Caphyon | `/i /qn` | Professional tool |
| **Wise** | Symantec | `/S` | Legacy, still common |

**InstallShield Detailed Switches:**

```cmd
:: Basic silent install
setup.exe /s /v"/qn"

::  With logging
setup.exe /s /v"/qn /l*v C:\Logs\install.log"

:: With reboot suppression
setup.exe /s /v"/qn REBOOT=ReallySuppress"

:: With custom properties
setup.exe /s /v"/qn INSTALLDIR=\"C:\Program Files\App\" ALLUSERS=1"

:: Response file method
setup.exe /s /f1"C:\response. iss"

:: Record response file (for creating silent install)
setup.exe /r /f1"C:\response. iss"
```

**Inno Setup Detailed Switches:**

```cmd
:: Silent install
setup.exe /VERYSILENT /SUPPRESSMSGBOXES

:: With logging
setup.exe /VERYSILENT /SUPPRESSMSGBOXES /LOG="C:\Logs\install.log"

:: Custom directory
setup.exe /VERYSILENT /DIR="C:\CustomPath"

::  Suppress reboot
setup.exe /VERYSILENT /NORESTART

:: All common switches
setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SP- /LOG="C:\Logs\install. log"
```

**NSIS Detailed Switches:**

```cmd
:: Silent install
setup.exe /S

:: Custom directory
setup.exe /S /D=C:\CustomPath

:: Note: /D must be last parameter
setup.exe /S /D=C:\Program Files\Application
```

**How to Identify Installer Type:**

```powershell
# Method 1: Check file properties
# Right-click EXE > Properties > Details > Look for "Product name" or "Company"

# Method 2: Run with /?  or --help
setup.exe /?
setup.exe --help
setup.exe /help
setup.exe -h

# Method 3: Extract and examine contents using 7-Zip
# Use 7-Zip to extract EXE and look for: 
# - setup.msi (InstallShield)
# - [0]. iss or install_script.iss (Inno Setup)
# - $PLUGINSDIR folder (NSIS)
# - WixCA.dll (WiX)

# Method 4: Use detection tools
# - Detect It Easy (DIE)
# - PEiD
# - ExeInfo PE
# - Universal Extractor

# Method 5: Check strings in executable
strings. exe setup.exe | findstr /i "inno nsis installshield wise"
```

**Installer Detection Script:**

```powershell
function Get-InstallerType {
    param([string]$FilePath)
    
    $bytes = [System.IO.File]::ReadAllBytes($FilePath)
    $content = [System.Text.Encoding]::ASCII.GetString($bytes)
    
    if ($content -match "Inno Setup") {
        return "Inno Setup"
    }
    elseif ($content -match "Nullsoft" -or $content -match "NSIS") {
        return "NSIS"
    }
    elseif ($content -match "InstallShield") {
        return "InstallShield"
    }
    elseif ($content -match "Windows Installer" -or $content -match "WiX") {
        return "WiX/MSI-based"
    }
    elseif ($content -match "Wise") {
        return "Wise Installer"
    }
    else {
        return "Unknown"
    }
}

# Usage
Get-InstallerType -FilePath "C:\Downloads\setup.exe"
```

##### 2.3 Other Package Formats

| Format | Description | Use Case |
|--------|-------------|----------|
| **.msix/. appx** | Modern Windows package format | UWP and modern Win32 apps |
| **. appv** | App-V virtualized package | Application virtualization |
| **.intunewin** | Intune Win32 package | Intune deployments |
| **.zip** | Compressed archive | Portable applications |
| **.msp** | MSI patch file | Updates to MSI packages |
| **.mst** | MSI transform file | MSI customization |
| **.cab** | Cabinet archive | Windows components, drivers |
| **.exe (SFX)** | Self-extracting archive | Portable installers |

#### Day 1 Practical Exercises

##### Exercise 1.1: Installer Identification (1 hour)

```
Task: Download the following applications and identify their installer types. 

Applications to analyze:
1. 7-Zip:  https://www.7-zip.org/
2. VLC Media Player: https://www.videolan.org/
3. Notepad++: https://notepad-plus-plus.org/
4. Adobe Reader DC: https://get.adobe.com/reader/
5. Google Chrome Enterprise: https://chromeenterprise.google/

For each application, document: 
┌─────────────────────────────────────────────────────────────────┐
│ Application Name:                                                 │
│ Version:                                                        │
│ Installer Type:                                                  │
│ File Name:                                                      │
│ File Size:                                                      │
│ Silent Install Command:                                         │
│ Silent Uninstall Command:                                       │
│ How You Identified the Type:                                    │
└─────────────────────────────────────────────────────────────────┘
```

##### Exercise 1.2: Manual Silent Installation (2 hours)

```
Task: Practice silent installations on your test VM.

Prerequisites:
- Clean Windows VM with snapshot
- Administrator access

Steps:
1. Create folder structure: 
   C:\Packages\
   C:\Packages\Downloads\
   C:\Packages\Logs\

2. Download 7-Zip MSI installer to C:\Packages\Downloads\

3. Open Command Prompt as Administrator

4. Execute silent installation:
   msiexec /i "C:\Packages\Downloads\7z2301-x64.msi" /qn /l*v "C:\Packages\Logs\7zip_install.log"

5. Verify installation:
   - Check Programs and Features
   - Check C:\Program Files\7-Zip exists
   - Run 7z.exe to confirm functionality

6. Execute silent uninstallation:
   msiexec /x {23170F69-40C1-2702-2301-000001000000} /qn /l*v "C:\Packages\Logs\7zip_uninstall.log"

7. Verify removal:
   - Check Programs and Features
   - Confirm folder removed

8. Review log files for any errors

9. Repeat process with 2 additional applications
```

##### Exercise 1.3: Documentation Practice (1 hour)

```
Task: Create professional installation documentation for 7-Zip.

Template to complete: 

═══════════════════════════════════════════════════════════════════
                    APPLICATION PACKAGING DOCUMENT
═══════════════════════════════════════════════════════════════════

GENERAL INFORMATION
───────────────────────────────────────────────────────────────────
Application Name:        
Version:               
Vendor:                
Website:               
Download URL:          
License Type:          
Package Date:          
Packager Name:         

INSTALLER DETAILS
───────────────────────────────────────────────────────────────────
Installer Type:        
File Name:             
File Size:             
MD5 Hash:              
SHA256 Hash:           

INSTALLATION COMMANDS
───────────────────────────────────────────────────────────────────
Silent Install:         
Silent Uninstall:       
Repair Command:        

INSTALLATION PATHS
───────────────────────────────────────────────────────────────────
Default Install Dir:   
Configuration Files:   
Log Files:             

DETECTION METHOD
───────────────────────────────────────────────────────────────────
Method Type:           [File/Registry/MSI Code]
Detection Path:        
Expected Value:        

DEPENDENCIES
───────────────────────────────────────────────────────────────────
Prerequisites:         
Runtime Requirements:  

TESTING RESULTS
───────────────────────────────────────────────────────────────────
Install Test:          [Pass/Fail]
Uninstall Test:        [Pass/Fail]
Functionality Test:    [Pass/Fail]
Notes:                 

═══════════════════════════════════════════════════════════════════
```

---

### Day 2: Windows Operating System Fundamentals for Packagers

#### Morning Session (4 hours): File System Deep Dive

##### 3.1 Windows Directory Structure

```
C:\
├── Program Files\                    # 64-bit applications (on 64-bit Windows)
│   ├── Common Files\                # Shared components
│   │   ├── Microsoft Shared\        # Microsoft shared files
│   │   └── System\                  # System shared files
│   └── [Application Folders]\       # Individual applications
│
├── Program Files (x86)\              # 32-bit applications (on 64-bit Windows)
│   ├── Common Files\                # 32-bit shared components
│   └── [Application Folders]\       # Individual 32-bit applications
│
├── ProgramData\                      # Application data for all users (hidden)
│   ├── Microsoft\                   # Microsoft application data
│   └── [Application Data]\          # Configs, caches, databases
│
├── Users\
│   ├── [Username]\
│   │   ├── AppData\                 # User-specific application data
│   │   │   ├── Local\               # Non-roaming data (caches, temp)
│   │   │   │   ├── Programs\        # Per-user installed apps
│   │   │   │   ├── Temp\            # User temporary files
│   │   │   │   └── Microsoft\       # Microsoft app data
│   │   │   ├── LocalLow\            # Low integrity data (sandboxed apps)
│   │   │   └── Roaming\             # Roaming profile data (synced)
│   │   ├── Desktop\                 # User desktop
│   │   ├── Documents\               # User documents
│   │   ├── Downloads\               # User downloads
│   │   └── [Other User Folders]\
│   │
│   ├── Default\                     # Template for new user profiles
│   └── Public\                      # Shared content for all users
│       ├── Desktop\                 # Public desktop items
│       └── Documents\               # Public documents
│
├── Windows\
│   ├── System32\                    # 64-bit system files (on 64-bit Windows)
│   │   ├── config\                  # Registry hives
│   │   ├── drivers\                 # System drivers
│   │   └── WindowsPowerShell\       # PowerShell
│   ├── SysWOW64\                    # 32-bit system files on 64-bit Windows
│   ├── Temp\                        # System temporary files
│   ├── Installer\                   # MSI cache (hidden, system)
│   ├── Logs\                        # System logs
│   ├── WinSxS\                      # Component store (side-by-side)
│   └── Prefetch\                    # Application prefetch data
│
└── Temp\                             # Additional system temp folder
```

**Critical Folders for Packagers:**

| Folder | Environment Variable | Purpose | Installation Context |
|--------|---------------------|---------|---------------------|
| `C:\Program Files` | `%ProgramFiles%` | 64-bit application installation | System |
| `C:\Program Files (x86)` | `%ProgramFiles(x86)%` | 32-bit application installation | System |
| `C:\ProgramData` | `%ProgramData%` | Shared app data, configs | System |
| `C:\Users\[User]\AppData\Local` | `%LocalAppData%` | User-specific non-roaming data | User |
| `C:\Users\[User]\AppData\Roaming` | `%AppData%` | User-specific roaming data | User |
| `C:\Users\[User]\AppData\LocalLow` | `%LocalAppData%Low` | Low integrity app data | User |
| `C:\Windows\Temp` | `%Temp%` (system context) | System temp files | System |
| `C:\Users\[User]\AppData\Local\Temp` | `%Temp%` (user context) | User temp files | User |
| `C:\Windows\System32` | `%SystemRoot%\System32` | 64-bit system binaries | System |
| `C:\Windows\SysWOW64` | `%SystemRoot%\SysWOW64` | 32-bit system binaries | System |

##### 3.2 Environment Variables

**System vs User Environment Variables:**

```
┌────────────────────────────────────────────────────────────────────────┐
│                        Environment Variables                            │
├────────────────────────────────┬───────────────────────────────────────┤
│   System Variables             │   User Variables                      │
│   (Apply to all users)         │   (Apply to current user only)        │
├────────────────────────────────┼───────────────────────────────────────┤
│ %SystemRoot% = C:\Windows      │ %UserProfile% = C:\Users\JohnDoe      │
│ %ProgramFiles% = C:\Program...  │ %AppData% = C:\Users\JD\AppData\Roam.  │
│ %ProgramFiles(x86)% = C:\Pr... │ %LocalAppData% = C:\Users\JD\AppData.. │
│ %CommonProgramFiles% = ...      │ %Temp% = C:\Users\JD\AppData\Local\T.. │
│ %SystemDrive% = C:             │ %HomeDrive% = C:                      │
│ %ComSpec% = C:\Windows\Sys...  │ %HomePath% = \Users\JohnDoe           │
│ %WinDir% = C:\Windows          │ %UserName% = JohnDoe                  │
│ %Path% (system portion)        │ %Path% (user portion)                 │
│ %ProgramData% = C:\ProgramData │                                       │
│ %PROCESSOR_ARCHITECTURE%       │                                       │
└────────────────────────────────┴───────────────────────────────────────┘
```

**Complete Environment Variable Reference:**

```powershell
# ============================================
# VIEWING ENVIRONMENT VARIABLES
# ============================================

# View all environment variables
Get-ChildItem Env: 

# View specific variable
$env:ProgramFiles
$env: PROCESSOR_ARCHITECTURE

# View in Command Prompt
set
echo %ProgramFiles%

# ============================================
# COMMON VARIABLES USED IN PACKAGING
# ============================================

# System paths
$env:ProgramFiles              # C:\Program Files
${env:ProgramFiles(x86)}       # C:\Program Files (x86) - Note special syntax
$env:ProgramData               # C:\ProgramData
$env:SystemRoot                # C:\Windows
$env:WinDir                    # C:\Windows
$env:SystemDrive               # C:
$env:CommonProgramFiles        # C:\Program Files\Common Files
${env:CommonProgramFiles(x86)} # C:\Program Files (x86)\Common Files

# User paths
$env:UserProfile               # C:\Users\Username
$env:AppData                   # C:\Users\Username\AppData\Roaming
$env:LocalAppData              # C:\Users\Username\AppData\Local
$env:Temp                      # Varies by context
$env: Tmp                       # Same as Temp

# Computer/user info
$env:ComputerName              # DESKTOP-ABC123
$env:UserName                  # CurrentUser
$env:UserDomain                # DOMAIN or COMPUTERNAME
$env:LogonServer               # \\DC01

# Architecture
$env:PROCESSOR_ARCHITECTURE    # AMD64 or x86
$env:PROCESSOR_ARCHITEW6432    # AMD64 (when 32-bit process on 64-bit OS)

# ============================================
# USING VARIABLES IN SCRIPTS
# ============================================

# PowerShell - Building paths
$installPath = Join-Path $env:ProgramFiles "MyApplication"
$configPath = Join-Path $env:ProgramData "MyApplication\config. xml"
$userDataPath = Join-Path $env: LocalAppData "MyApplication"
$logPath = Join-Path $env: Temp "MyApplication_Install.log"

# PowerShell - Conditional paths based on architecture
if ($env:PROCESSOR_ARCHITECTURE -eq "AMD64") {
    $installPath = Join-Path $env:ProgramFiles "MyApplication"
} else {
    $installPath = Join-Path ${env:ProgramFiles(x86)} "MyApplication"
}

# Batch - Building paths
set INSTALLPATH=%ProgramFiles%\MyApplication
set CONFIGPATH=%ProgramData%\MyApplication\config.xml
set USERDATAPATH=%LocalAppData%\MyApplication
set LOGPATH=%Temp%\MyApplication_Install.log

# ============================================
# SETTING ENVIRONMENT VARIABLES
# ============================================

# PowerShell - Session only
$env:MyVariable = "MyValue"

# PowerShell - Permanent (User)
[Environment]::SetEnvironmentVariable("MyVariable", "MyValue", "User")

# PowerShell - Permanent (System) - Requires Admin
[Environment]::SetEnvironmentVariable("MyVariable", "MyValue", "Machine")

# Command Prompt - Permanent
setx MyVariable "MyValue"           # User
setx MyVariable "MyValue" /M        # System (requires Admin)
```

##### 3.3 Installation Contexts

**System Context vs User Context:**

| Aspect | System Context | User Context |
|--------|---------------|--------------|
| **Runs as** | SYSTEM account (NT AUTHORITY\SYSTEM) | Current logged-in user |
| **Permissions** | Full admin rights, highest privileges | User's rights (may be limited) |
| **Registry access** | HKLM (full), HKU (all users) | HKCU (current user), limited HKLM |
| **File access** | All locations | User profile + public + permitted locations |
| **%Temp%** | C:\Windows\Temp | C:\Users\[User]\AppData\Local\Temp |
| **%AppData%** | C:\Windows\System32\config\systemprofile\AppData\Roaming | C:\Users\[User]\AppData\Roaming |
| **Network access** | No mapped drives, no user credentials | User's mapped drives and credentials |
| **User profile** | No access to user profiles | Full access to current user's profile |
| **Common use** | Required deployments (SCCM, Intune) | Available/self-service apps, user-installed |
| **SCCM default** | Yes (Install for system) | Optional (Install for user) |
| **Intune default** | System context | User context optional |

**Context Comparison Diagram:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         SYSTEM CONTEXT                                   │
│                    (NT AUTHORITY\SYSTEM)                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✓ Full administrator rights                                            │
│  ✓ Access to HKEY_LOCAL_MACHINE                                         │
│  ✓ Access to C:\Program Files                                           │
│  ✓ Access to C:\ProgramData                                             │
│  ✓ Access to C:\Windows                                                 │
│  ✓ Can install for all users                                            │
│                                                                          │
│  ✗ NO access to user profiles (C:\Users\*)                              │
│  ✗ NO network drives (Z:\, H:\, etc.)                                   │
│  ✗ NO user credentials for network resources                            │
│  ✗ NO HKEY_CURRENT_USER of logged-in user                               │
│                                                                          │
│  %Temp% = C:\Windows\Temp                                               │
│  %AppData% = C:\Windows\System32\config\systemprofile\AppData\Roaming   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                          USER CONTEXT                                    │
│                        (DOMAIN\Username)                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✓ Access to HKEY_CURRENT_USER                                          │
│  ✓ Access to user profile (C:\Users\Username)                           │
│  ✓ Access to user's AppData folders                                     │
│  ✓ Network drives available                                             │
│  ✓ User credentials for network resources                               │
│                                                                          │
│  ✗ Limited HKEY_LOCAL_MACHINE access                                    │
│  ✗ Cannot write to C:\Program Files (without elevation)                 │
│  ✗ Cannot install for other users                                       │
│  ✗ Cannot modify system services                                        │
│                                                                          │
│  %Temp% = C:\Users\Username\AppData\Local\Temp                          │
│  %AppData% = C:\Users\Username\AppData\Roaming                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Why Context Matters - Common Issues:**

```powershell
# ============================================
# PROBLEM: Script works manually but fails in SCCM
# ============================================

# SCENARIO:  You test a script logged in as admin, it works. 
# Deploy via SCCM, it fails.  Why? 

# Manual execution (user context):
# - %Temp% = C:\Users\JohnDoe\AppData\Local\Temp
# - Has access to user's profile
# - Network drives may be mapped (H:\, Z:\, etc.)
# - Can prompt for user input

# SCCM execution (system context):
# - %Temp% = C:\Windows\Temp
# - NO user profile access
# - NO network drive access
# - NO user interaction possible

# ============================================
# SOLUTION: Context-aware scripting
# ============================================

# DON'T DO THIS:
$config = "H:\MyConfig.xml"  # Network drive - won't exist in system context! 
Copy-Item $config -Destination $env:AppData  # AppData is different in system context! 

# DO THIS INSTEAD:
$config = "\\server\share\configs\MyConfig.xml"  # UNC path
$destination = "C:\ProgramData\MyApplication"    # Explicit path, not variable
Copy-Item $config -Destination $destination

# ============================================
# DETECTING CONTEXT IN SCRIPTS
# ============================================

function Get-InstallationContext {
    $currentUser = [System.Security.Principal.WindowsIdentity]::GetCurrent()
    
    if ($currentUser.Name -eq "NT AUTHORITY\SYSTEM") {
        return "System"
    }
    elseif ($currentUser.Name -like "*\*") {
        return "User"
    }
    else {
        return "Unknown"
    }
}

# Determine if running as admin
function Test-Administrator {
    $currentPrincipal = New-Object Security.Principal.WindowsPrincipal(
        [Security.Principal.WindowsIdentity]::GetCurrent()
    )
    return $currentPrincipal.IsInRole(
        [Security.Principal.WindowsBuiltInRole]::Administrator
    )
}

# Example usage
$context = Get-InstallationContext
$isAdmin = Test-Administrator

Write-Host "Running in: $context context"
Write-Host "Is Administrator: $isAdmin"

if ($context -eq "System") {
    $logPath = "C:\Windows\Temp\install. log"
    $dataPath = "C:\ProgramData\MyApp"
} else {
    $logPath = "$env:Temp\install.log"
    $dataPath = "$env:LocalAppData\MyApp"
}
```

#### Afternoon Session (4 hours): Windows Registry Deep Dive

##### 4.1 Registry Structure

```
Windows Registry
│
├── HKEY_CLASSES_ROOT (HKCR)         # File associations, COM objects
│   │                                 # Merged view of HKLM\SOFTWARE\Classes
│   │                                 # and HKCU\SOFTWARE\Classes
│   ├── . txt                          # File extension associations
│   ├── . doc                          # Maps extension to file type
│   ├── txtfile                       # File type definitions
│   ├── Word.Document.12              # Application file types
│   ├── CLSID                         # COM class identifiers (GUIDs)
│   │   └── {GUID}\                   # Individual COM objects
│   │       ├── InprocServer32        # DLL path for COM object
│   │       └── LocalServer32         # EXE path for COM object
│   └── Installer                     # Windows Installer data
│       ├── Products                  # Installed products
│       └── Features                  # Installed features
│
├── HKEY_CURRENT_USER (HKCU)          # Current user's settings
│   │                                 # Loaded from NTUSER.DAT in user profile
│   ├── Software                      # User application settings
│   │   ├── Microsoft                 # Microsoft application settings
│   │   │   ├── Office                # Office settings
│   │   │   └── Windows               # Windows settings
│   │   │       └── CurrentVersion
│   │   │           ├── Run           # User startup programs
│   │   │           └── Explorer      # Explorer settings
│   │   └── [Vendor]                  # Third-party app settings
│   │       └── [Application]         # Specific app settings
│   ├── Environment                   # User environment variables
│   ├── Control Panel                 # User preferences
│   └── Volatile Environment          # Session-specific data
│
├── HKEY_LOCAL_MACHINE (HKLM)         # Machine-wide settings
│   │                                 # System configuration
│   ├── SOFTWARE                      # Installed software settings
│   │   ├── Microsoft                 # Microsoft software
│   │   │   ├── Windows               
│   │   │   │   └── CurrentVersion
│   │   │   │       ├── Uninstall     # 64-bit uninstall entries ← IMPORTANT
│   │   │   │       ├── Run           # 64-bit startup programs
│   │   │   │       ├── RunOnce       # One-time startup programs
│   │   │   │       ├── App Paths     # Application paths
│   │   │   │       └── Installer     # Windows Installer data
│   │   │   │           ├── UserData  # Per-user installer data
│   │   │   │           └── Products  # Product registration
│   │   │   ├── . NET Framework        # .NET settings
│   │   │   └── Office                # Office machine settings
│   │   │
│   │   ├── WOW6432Node               # 32-bit software on 64-bit OS
│   │   │   └── Microsoft             # (Registry redirection)
│   │   │       └── Windows
│   │   │           └── CurrentVersion
│   │   │               └── Uninstall # 32-bit uninstall entries ← IMPORTANT
│   │   │
│   │   ├── Classes                   # Machine file associations
│   │   └── [Vendor]                  # Third-party software
│   │       └── [Application]         # Application settings
│   │
│   ├── SYSTEM                        # System configuration
│   │   ├── CurrentControlSet         # Current boot configuration
│   │   │   ├── Control               # System control parameters
│   │   │   │   └── Session Manager
│   │   │   │       └── Environment   # System environment variables
│   │   │   ├── Services              # Windows services ← IMPORTANT
│   │   │   │   └── [ServiceName]     # Individual service config
│   │   │   │       ├── Start         # Startup type
│   │   │   │       ├── Type          # Service type
│   │   │   │       └── ImagePath     # Path to service executable
│   │   │   └── Enum                  # Hardware enumeration
│   │   ├── ControlSet001             # Boot configuration 1
│   │   └── ControlSet002             # Boot configuration 2
│   │
│   ├── HARDWARE                      # Hardware configuration (volatile)
│   │   └── DESCRIPTION               # Hardware description
│   │
│   └── SECURITY                      # Security configuration (restricted)
│
├── HKEY_USERS (HKU)                  # All loaded user profiles
│   ├── . DEFAULT                      # Default profile template
│   ├── S-1-5-18                      # SYSTEM account
│   ├── S-1-5-19                      # LOCAL SERVICE account
│   ├── S-1-5-20                      # NETWORK SERVICE account
│   └── S-1-5-21-.. .-1001             # User SIDs (logged-in users)
│       └── [Same structure as HKCU]
│
└── HKEY_CURRENT_CONFIG (HKCC)        # Current hardware profile
    └── [Hardware config data]         # (Rarely used in packaging)
```

##### 4.2 Critical Registry Locations for Packagers

**Uninstall Registry Keys (MOST IMPORTANT):**

```
# 64-bit applications on 64-bit Windows: 
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{GUID or Name}

# 32-bit applications on 64-bit Windows:
HKLM\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\{GUID or Name}

# Per-user installations:
HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{GUID or Name}

# Key naming: 
# - MSI products use ProductCode GUID:  {12345678-1234-1234-1234-123456789012}
# - Non-MSI products often use application name: ApplicationName
```

**Uninstall Key Values:**

| Value Name | Type | Description | Example |
|------------|------|-------------|---------|
| DisplayName | REG_SZ | Application name shown in Programs | "7-Zip 23.01 (x64)" |
| DisplayVersion | REG_SZ | Version number | "23.01" |
| Publisher | REG_SZ | Vendor name | "Igor Pavlov" |
| InstallDate | REG_SZ | Installation date (YYYYMMDD) | "20231215" |
| InstallLocation | REG_SZ | Installation path | "C:\Program Files\7-Zip" |
| InstallSource | REG_SZ | Source path of installer | "C:\Temp\" |
| UninstallString | REG_SZ | Uninstall command | "MsiExec. exe /X{23170F69... }" |
| QuietUninstallString | REG_SZ | Silent uninstall command | "MsiExec.exe /X{... } /qn" |
| ModifyPath | REG_SZ | Modify/change command | "MsiExec.exe /I{... }" |
| EstimatedSize | REG_DWORD | Size in KB | 5120 |
| NoModify | REG_DWORD | Hide Modify button | 1 |
| NoRepair | REG_DWORD | Hide Repair button | 1 |
| NoRemove | REG_DWORD | Hide Remove button | 1 |
| SystemComponent | REG_DWORD | Hide from Programs list | 1 |
| WindowsInstaller | REG_DWORD | Is MSI product | 1 |
| VersionMajor | REG_DWORD | Major version | 23 |
| VersionMinor | REG_DWORD | Minor version | 1 |
| Language | REG_DWORD | Language code | 1033 (English) |

##### 4.3 PowerShell Registry Operations

```powershell
# ============================================
# READING REGISTRY VALUES
# ============================================

# Get all 64-bit uninstall entries
$uninstall64 = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*"
Get-ItemProperty $uninstall64 | 
    Select-Object DisplayName, DisplayVersion, Publisher, InstallLocation |
    Sort-Object DisplayName

# Get all 32-bit uninstall entries
$uninstall32 = "HKLM:\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*"
Get-ItemProperty $uninstall32 | 
    Select-Object DisplayName, DisplayVersion, Publisher, InstallLocation |
    Sort-Object DisplayName

# Get per-user uninstall entries
$uninstallUser = "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*"
Get-ItemProperty $uninstallUser | 
    Select-Object DisplayName, DisplayVersion, Publisher |
    Sort-Object DisplayName

# Find specific application
Get-ItemProperty $uninstall64 | Where-Object { $_.DisplayName -like "*7-Zip*" }

# Get all applications from a specific publisher
Get-ItemProperty $uninstall64, $uninstall32 -ErrorAction SilentlyContinue | 
    Where-Object { $_.Publisher -like "*Microsoft*" } |
    Select-Object DisplayName, DisplayVersion, Publisher

# Get specific registry value
$regPath = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{23170F69-40C1-2702-2301-000001000000}"
$displayVersion = (Get-ItemProperty -Path $regPath -ErrorAction SilentlyContinue).DisplayVersion
Write-Host "Version: $displayVersion"

# Read registry with error handling
try {
    $value = Get-ItemPropertyValue -Path $regPath -Name "DisplayVersion" -ErrorAction Stop
    Write-Host "Found version: $value"
}
catch {
    Write-Host "Registry key or value not found"
}

# ============================================
# WRITING REGISTRY VALUES
# ============================================

# Create new registry key
$appRegPath = "HKLM:\SOFTWARE\MyCompany\MyApplication"
New-Item -Path $appRegPath -Force | Out-Null

# Set string value (REG_SZ)
Set-ItemProperty -Path $appRegPath -Name "InstallPath" -Value "C:\Program Files\MyApp" -Type String

# Set expandable string value (REG_EXPAND_SZ) - allows environment variables
Set-ItemProperty -Path $appRegPath -Name "DataPath" -Value "%ProgramData%\MyApp" -Type ExpandString

# Set DWORD value (REG_DWORD)
Set-ItemProperty -Path $appRegPath -Name "Version" -Value 1 -Type DWord
Set-ItemProperty -Path $appRegPath -Name "Installed" -Value 1 -Type DWord

# Set QWORD value (REG_QWORD) - 64-bit integer
Set-ItemProperty -Path $appRegPath -Name "InstallTime" -Value ([DateTime]::Now. Ticks) -Type QWord

# Set multi-string value (REG_MULTI_SZ)
Set-ItemProperty -Path $appRegPath -Name "Features" -Value @("Feature1", "Feature2", "Feature3") -Type MultiString

# Set binary value (REG_BINARY)
Set-ItemProperty -Path $appRegPath -Name "BinaryData" -Value ([byte[]](0x01, 0x02, 0x03, 0x04)) -Type Binary

# ============================================
# CREATING UNINSTALL ENTRY
# ============================================

$uninstallPath = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\MyApplication"
New-Item -Path $uninstallPath -Force | Out-Null

$uninstallProperties = @{
    DisplayName = "My Application"
    DisplayVersion = "1.0.0"
    Publisher = "My Company"
    InstallLocation = "C:\Program Files\MyApplication"
    InstallDate = (Get-Date -Format "yyyyMMdd")
    UninstallString = "C:\Program Files\MyApplication\uninstall.exe"
    QuietUninstallString = "C:\Program Files\MyApplication\uninstall.exe /S"
    NoModify = 1
    NoRepair = 1
    EstimatedSize = 10240  # in KB
}

foreach ($property in $uninstallProperties.GetEnumerator()) {
    if ($property.Value -is [int]) {
        Set-ItemProperty -Path $uninstallPath -Name $property.Key -Value $property.Value -Type DWord
    } else {
        Set-ItemProperty -Path $uninstallPath -Name $property.Key -Value $property.Value -Type String
    }
}

# ============================================
# DELETING REGISTRY VALUES
# ============================================

# Remove a specific value
Remove-ItemProperty -Path $appRegPath -Name "OldValue" -ErrorAction SilentlyContinue

# Remove entire key and all subkeys
Remove-Item -Path $appRegPath -Recurse -Force -ErrorAction SilentlyContinue

# ============================================
# TESTING REGISTRY (for detection methods)
# ============================================

# Test if key exists
$keyExists = Test-Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{23170F69-40C1-2702-2301-000001000000}"
Write-Host "Key exists: $keyExists"

# Test if value exists
$valueName = "DisplayVersion"
$key = Get-Item -Path $regPath -ErrorAction SilentlyContinue
$valueExists = $key. GetValueNames() -contains $valueName
Write-Host "Value exists: $valueExists"

# Test if value matches expected
function Test-RegistryValue {
    param(
        [string]$Path,
        [string]$Name,
        [string]$ExpectedValue,
        [string]$Operator = "eq"  # eq, ge, le, like
    )
    
    try {
        $actualValue = Get-ItemPropertyValue -Path $Path -Name $Name -ErrorAction Stop
        
        switch ($Operator) {
            "eq" { return $actualValue -eq $ExpectedValue }
            "ge" { return [version]$actualValue -ge [version]$ExpectedValue }
            "le" { return [version]$actualValue -le [version]$ExpectedValue }
            "like" { return $actualValue -like $ExpectedValue }
            default { return $actualValue -eq $ExpectedValue }
        }
    }
    catch {
        return $false
    }
}

# Example detection script
$detected = Test-RegistryValue -Path $regPath -Name "DisplayVersion" -ExpectedValue "23.01" -Operator "ge"
if ($detected) {
    Write-Host "Application detected - version 23.01 or higher installed"
    exit 0
} else {
    Write-Host "Application not detected"
    exit 1
}

# ============================================
# REGISTRY REDIRECTION (32-bit vs 64-bit)
# ============================================

# When running 32-bit PowerShell on 64-bit Windows:
# HKLM:\SOFTWARE is redirected to HKLM:\SOFTWARE\WOW6432Node

# To access the actual 64-bit registry from 32-bit process:
$reg64 = [Microsoft.Win32.RegistryKey]::OpenBaseKey(
    [Microsoft.Win32.RegistryHive]::LocalMachine,
    [Microsoft.Win32.RegistryView]::Registry64
)
$subKey = $reg64.OpenSubKey("SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall")

# To access the actual 32-bit registry from 64-bit process: 
$reg32 = [Microsoft. Win32.RegistryKey]::OpenBaseKey(
    [Microsoft.Win32.RegistryHive]::LocalMachine,
    [Microsoft.Win32.RegistryView]::Registry32
)
$subKey = $reg32.OpenSubKey("SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall")

# Check which PowerShell architecture you're running
if ([Environment]::Is64BitProcess) {
    Write-Host "Running 64-bit PowerShell"
} else {
    Write-Host "Running 32-bit PowerShell"
}
```

#### Day 2 Practical Exercises

##### Exercise 2.1: File System Exploration (1 hour)

```powershell
# Complete these tasks and document findings: 

# Task 1: List all folders in Program Files
Write-Host "=== 64-bit Program Files ===" -ForegroundColor Cyan
Get-ChildItem "C:\Program Files" -Directory | 
    Select-Object Name, CreationTime |
    Format-Table -AutoSize

# Task 2: List all folders in Program Files (x86)
Write-Host "=== 32-bit Program Files ===" -ForegroundColor Cyan
Get-ChildItem "C:\Program Files (x86)" -Directory |
    Select-Object Name, CreationTime |
    Format-Table -AutoSize

# Task 3: List contents of ProgramData (including hidden)
Write-Host "=== ProgramData Contents ===" -ForegroundColor Cyan
Get-ChildItem "C:\ProgramData" -Force -Directory |
    Select-Object Name, Attributes, CreationTime |
    Format-Table -AutoSize

# Task 4: Find all executable files in a specific application folder
Write-Host "=== Executables in 7-Zip folder ===" -ForegroundColor Cyan
Get-ChildItem "C:\Program Files\7-Zip" -Recurse -Filter "*.exe" |
    Select-Object Name, Length, VersionInfo |
    Format-Table -AutoSize

# Task 5: Calculate total size of an application folder
$folder = "C:\Program Files\7-Zip"
$size = (Get-ChildItem $folder -Recurse -ErrorAction SilentlyContinue | 
    Measure-Object -Property Length -Sum).Sum
Write-Host "Total size of $folder`: $([math]::Round($size / 1MB, 2)) MB" -ForegroundColor Green

# Task 6: Find all config files in application folders
Write-Host "=== Configuration Files ===" -ForegroundColor Cyan
Get-ChildItem "C:\Program Files\7-Zip" -Recurse -Include "*.cfg","*.ini","*.xml","*.config" |
    Select-Object FullName, Length |
    Format-Table -AutoSize

# Task 7: Export application inventory to CSV
$allApps = Get-ChildItem "C:\Program Files", "C:\Program Files (x86)" -Directory -ErrorAction SilentlyContinue
$allApps | Select-Object FullName, Name, CreationTime | 
    Export-Csv "C:\Temp\InstalledAppFolders.csv" -NoTypeInformation
Write-Host "Exported to C:\Temp\InstalledAppFolders.csv" -ForegroundColor Green
```

##### Exercise 2.2: Registry Exploration (1.5 hours)

```powershell
# Complete these tasks: 

# Task 1: Export all uninstall entries to CSV
$uninstall64 = Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*" -ErrorAction SilentlyContinue
$uninstall32 = Get-ItemProperty "HKLM:\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*" -ErrorAction SilentlyContinue

$allApps = @()
$allApps += $uninstall64 | Select-Object @{N='Architecture';E={'64-bit'}}, DisplayName, DisplayVersion, Publisher, InstallLocation, UninstallString
$allApps += $uninstall32 | Select-Object @{N='Architecture';E={'32-bit'}}, DisplayName, DisplayVersion, Publisher, InstallLocation, UninstallString

$allApps | Where-Object { $_.DisplayName } | 
    Sort-Object DisplayName |
    Export-Csv "C:\Temp\InstalledApplications.csv" -NoTypeInformation

Write-Host "Exported $($allApps.Count) applications to C:\Temp\InstalledApplications.csv"

# Task 2: Find all Microsoft applications with product codes
$msApps = $allApps | Where-Object { $_.Publisher -like "*Microsoft*" }
$msApps | Select-Object DisplayName, DisplayVersion | Format-Table -AutoSize

# Task 3: Create a custom registry key for practice
$testPath = "HKLM:\SOFTWARE\PackagingTraining"
New-Item -Path $testPath -Force | Out-Null
Set-ItemProperty -Path $testPath -Name "TraineeName" -Value "YourName" -Type String
Set-ItemProperty -Path $testPath -Name "TrainingDate" -Value (Get-Date -Format "yyyy-MM-dd") -Type String
Set-ItemProperty -Path $testPath -Name "CompletedExercises" -Value 0 -Type DWord
Set-ItemProperty -Path $testPath -Name "Notes" -Value "Registry exercise completed" -Type String

Write-Host "Created registry key at $testPath"
Get-ItemProperty $testPath | Format-List

# Task 4: Update the registry values
Set-ItemProperty -Path $testPath -Name "CompletedExercises" -Value 1 -Type DWord
Set-ItemProperty -Path $testPath -Name "LastUpdated" -Value (Get-Date -Format "yyyy-MM-dd HH:mm:ss") -Type String

Write-Host "Updated registry values:"
Get-ItemProperty $testPath | Format-List

# Task 5: Clean up - remove test registry key
Remove-Item -Path $testPath -Recurse -Force
Write-Host "Cleaned up test registry key"

# Task 6: Find specific application details
$appToFind = "7-Zip"
$found = $allApps | Where-Object { $_.DisplayName -like "*$appToFind*" }
if ($found) {
    Write-Host "=== $appToFind Details ===" -ForegroundColor Green
    $found | Format-List DisplayName, DisplayVersion, Publisher, InstallLocation, UninstallString
} else {
    Write-Host "$appToFind not found"
}
```

##### Exercise 2.3: Environment Variable Practice (30 minutes)

```powershell
# Task 1: Display all environment variables sorted
Write-Host "=== All Environment Variables ===" -ForegroundColor Cyan
Get-ChildItem Env: | Sort-Object Name | Format-Table Name, Value -AutoSize -Wrap

# Task 2: Create and test paths using environment variables
$paths = @(
    @{Name="64-bit Programs"; Path=(Join-Path $env:ProgramFiles "TestApp")},
    @{Name="32-bit Programs"; Path=(Join-Path ${env:ProgramFiles(x86)} "TestApp")},
    @{Name="ProgramData"; Path=(Join-Path $env: ProgramData "TestApp\Config")},
    @{Name="Local AppData"; Path=(Join-Path $env:LocalAppData "TestApp\Cache")},
    @{Name="Roaming AppData"; Path=(Join-Path $env:AppData "TestApp\Settings")},
    @{Name="Temp Folder"; Path=(Join-Path $env: TEMP "TestApp_Install")}
)

Write-Host "`n=== Path Resolution ===" -ForegroundColor Cyan
foreach ($item in $paths) {
    Write-Host "$($item.Name):" -ForegroundColor Yellow
    Write-Host "  Path: $($item.Path)"
    Write-Host "  Exists: $(Test-Path $item.Path)"
}

# Task 3: Detect system architecture
Write-Host "`n=== System Architecture ===" -ForegroundColor Cyan
Write-Host "PROCESSOR_ARCHITECTURE: $env:PROCESSOR_ARCHITECTURE"
Write-Host "Is 64-bit OS: $([Environment]::Is64BitOperatingSystem)"
Write-Host "Is 64-bit Process: $([Environment]::Is64BitProcess)"

# Task 4: Display Windows and user information
Write-Host "`n=== System Information ===" -ForegroundColor Cyan
Write-Host "Computer Name: $env:COMPUTERNAME"
Write-Host "User Name: $env:USERNAME"
Write-Host "User Domain: $env:USERDOMAIN"
Write-Host "Windows Directory: $env:WINDIR"
Write-Host "System Drive: $env: SYSTEMDRIVE"

# Task 5: Test context detection
Write-Host "`n=== Execution Context ===" -ForegroundColor Cyan
$identity = [System.Security.Principal.WindowsIdentity]::GetCurrent()
Write-Host "Running as: $($identity.Name)"

$principal = New-Object System.Security.Principal. WindowsPrincipal($identity)
$isAdmin = $principal.IsInRole([System.Security.Principal.WindowsBuiltInRole]::Administrator)
Write-Host "Is Administrator: $isAdmin"

if ($identity.Name -eq "NT AUTHORITY\SYSTEM") {
    Write-Host "Context:  SYSTEM (deployment context)" -ForegroundColor Yellow
} else {
    Write-Host "Context: USER (interactive context)" -ForegroundColor Green
}
```

---

### Day 3: Windows Services, Processes, and Permissions

#### Morning Session (4 hours): Windows Services

##### 5.1 Understanding Windows Services

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          Windows Services                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Services are background processes that:                                  │
│  • Start automatically with Windows (or manually/on-demand)             │
│  • Run without user interaction                                         │
│  • Continue running even when no user is logged in                      │
│  • Can run under different security contexts (SYSTEM, Network, etc.)    │
│  • Managed by the Service Control Manager (SCM)                         │
│                                                                          │
│  Registry Location: HKLM\SYSTEM\CurrentControlSet\Services              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Service Startup Types:**

| Startup Type | Value | Description | When to Use |
|--------------|-------|-------------|-------------|
| **Automatic
