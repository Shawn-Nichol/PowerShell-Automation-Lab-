# Get-ComputerInfo

## Executive Summary

- `Get-ComputerInfo` retrieves detailed information about a Windows computer, including operating system, hardware, BIOS, and security configuration details.
- The cmdlet returns a PowerShell object containing hundreds of properties that can be filtered and examined.
- Property prefixes help categorize information:
  - `Windows*` = Windows product information
  - `Os*` = Operating system details
  - `Cs*` = Computer system and hardware information
  - `Bios*` = BIOS/UEFI information
- `Select-Object` can be used to display only relevant properties.
- `Get-Member` is the preferred method for discovering available properties and understanding returned objects.

---

## Objective

Explore the `Get-ComputerInfo` cmdlet to understand how PowerShell exposes operating system and hardware information through objects.

---

## Command Syntax

```powershell
Get-ComputerInfo
```

---

## Description

`Get-ComputerInfo` gathers information from multiple areas of Windows and returns it as a single PowerShell object.

Information available includes:

- Operating System Details
- Computer Hardware Information
- BIOS/UEFI Information
- Security Configuration
- Device Guard Status
- Memory Configuration
- Processor Information
- Time Zone Settings

Unlike traditional command-line tools that return text, `Get-ComputerInfo` returns structured data that can be filtered, exported, and manipulated.

---

## Key Properties

### Windows Properties

Properties related to the Windows product and feature release.

```text
WindowsProductName
WindowsVersion
```

Example:

```text
WindowsProductName : Windows 11 Enterprise
WindowsVersion     : 24H2
```

---

### Operating System Properties

Technical details about the operating system.

```text
OsVersion
OsBuildNumber
OsArchitecture
```

Example:

```text
OsVersion      : 10.0.26100
OsBuildNumber  : 26100
OsArchitecture : 64-bit
```

---

### Computer System Properties

Hardware and system inventory information.

```text
CsName
CsManufacturer
CsModel
CsTotalPhysicalMemory
```

Common uses include asset management and inventory reporting.

---

### BIOS Properties

Firmware information.

```text
BiosManufacturer
BiosVersion
```

These properties can be useful when verifying firmware versions or troubleshooting hardware issues.

---

### Security Properties

Information related to Windows security features.

```text
DeviceGuardSecurityServicesRunning
DeviceGuardSmartStatus
```

Useful for understanding security capabilities and configurations.

---

## Examples

### Display All Computer Information

```powershell
Get-ComputerInfo
```

Displays all available properties.

---

### Display Selected Operating System Properties

```powershell
Get-ComputerInfo |
Select-Object WindowsProductName,
              WindowsVersion,
              OsVersion,
              OsBuildNumber,
              OsArchitecture
```

Useful when inventorying systems or verifying operating system versions.

---

### Display Hardware Information

```powershell
Get-ComputerInfo |
Select-Object CsName,
              CsManufacturer,
              CsModel,
              CsTotalPhysicalMemory
```

Useful for gathering hardware inventory information.

---

### Discover Available Properties

```powershell
Get-ComputerInfo | Get-Member
```

Displays all available properties and methods associated with the returned object.

---

### Find All Computer System Properties

```powershell
Get-ComputerInfo | Select-Object Cs*
```

Displays only hardware-related information.

---

## Key Learnings

### Understanding Property Prefixes

One of the most useful discoveries was that many properties are grouped using common prefixes.

| Prefix | Purpose |
|----------|----------|
| Windows* | Windows product information |
| Os* | Operating system details |
| Cs* | Computer system and hardware details |
| Bios* | BIOS and firmware information |
| DeviceGuard* | Security-related information |

Recognizing these prefixes makes it easier to discover information without scrolling through hundreds of properties.

---

### Windows Version vs OS Version

Initially there was confusion between Windows version information and operating system version information.

The following properties represent different concepts:

| Property | Meaning |
|-----------|----------|
| WindowsProductName | Product name of Windows |
| WindowsVersion | Feature update version (e.g., 24H2) |
| OsVersion | Technical operating system version |
| OsBuildNumber | Specific build number |
| OsArchitecture | Operating system architecture |

Example:

```text
WindowsProductName : Windows 11 Enterprise
WindowsVersion     : 24H2
OsVersion          : 10.0.26100
OsBuildNumber      : 26100
OsArchitecture     : 64-bit
```

---

### Build Numbers Matter

While Windows versions are useful for identifying releases, the build number provides a more precise identification of the installed operating system.

Build numbers are commonly used when:

- Troubleshooting issues
- Verifying updates
- Confirming software compatibility
- Identifying known bugs and fixes

---

## Real-World Use Cases

### System Inventory

Gather information for asset tracking and documentation.

```powershell
Get-ComputerInfo |
Select-Object CsName,
              CsManufacturer,
              CsModel,
              WindowsProductName,
              OsBuildNumber
```

---

### Upgrade Planning

Identify operating system versions and build numbers before rolling out updates.

---

### Troubleshooting

Use build numbers, BIOS versions, and hardware information when diagnosing problems.

---

### Compliance Auditing

Collect operating system and security-related information for reporting and validation purposes.

---

## Common Mistakes

### Mistake #1: Treating Build Numbers as Hardware Models

Incorrect:

```text
OsBuildNumber = Hardware Model
```

Correct:

```text
OsBuildNumber = Operating System Build
CsModel       = Hardware Model
```

Hardware model information is located in `CsModel`.

---

### Mistake #2: Scrolling Through All Properties

The full output contains hundreds of properties.

Instead, filter information using prefixes:

```powershell
Get-ComputerInfo | Select-Object Os*
```

or

```powershell
Get-ComputerInfo | Select-Object Cs*
```

This makes information easier to discover and understand.

---

### Mistake #3: Ignoring Object Exploration

Many users focus on memorizing commands instead of understanding what objects contain.

A better approach is:

```powershell
Get-ComputerInfo | Get-Member
```

This reveals the structure of the returned object.

---

## Related Commands

### Get-Member

Explore available properties and methods.

```powershell
Get-ComputerInfo | Get-Member
```

### Select-Object

Display only relevant properties.

```powershell
Get-ComputerInfo | Select-Object Os*
```

### Get-CimInstance

Retrieve detailed information from specific Windows management classes.

```powershell
Get-CimInstance Win32_ComputerSystem
```

---

## Reflection

This exercise reinforced one of the most important PowerShell concepts: commands return objects rather than text.

The most valuable lesson was learning to explore and understand object properties instead of attempting to memorize them. By identifying common property prefixes and using tools such as `Get-Member`, it becomes much easier to discover useful information and build future automation scripts.

Understanding the distinction between product information (`Windows*`), operating system details (`Os*`), hardware information (`Cs*`), and firmware information (`Bios*`) provides a strong foundation for future PowerShell exploration and system administration tasks.
