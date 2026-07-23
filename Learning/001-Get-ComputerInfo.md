<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/07d33edc-f088-430d-8a54-4c77b7605cf3" />


# Get-ComputerInfo

## 1. Executive Summary

`Get-ComputerInfo` is a PowerShell cmdlet that provides detailed information about a Windows system, including operating system details, hardware inventory, BIOS information, and security-related configuration. During this exercise, I learned how PowerShell organizes large amounts of system information into a single object and how object exploration techniques can be used to discover useful properties without relying on memorization.

### Highlights

- Learned the difference between Windows product information and operating system version information.
- Discovered how PowerShell organizes information using property prefixes such as `Windows*`, `Os*`, `Cs*`, and `Bios*`.
- Used `Select-Object` to filter large datasets into meaningful information.
- Used `Get-Member` to explore an unfamiliar object and discover available properties.
- Corrected the misconception that operating system build numbers represent hardware models.

---

## 2. Learning Objective

The goal of this exercise was to understand how PowerShell exposes system information and to become comfortable navigating large PowerShell objects.

Specific objectives included:

- Understanding the output of `Get-ComputerInfo`
- Identifying useful operating system properties
- Learning how to locate hardware information
- Practicing object discovery techniques
- Understanding the difference between Windows versions, operating system versions, and hardware models

---

## 3. Cybersecurity Applications

Although `Get-ComputerInfo` appears to be a simple inventory command, it has several cybersecurity applications.

### Host Enumeration

Security analysts often need to quickly understand the system they are investigating, including:

- Computer name
- Operating system version
- Build number
- Hardware platform

### Vulnerability Assessment

Operating system versions and build numbers help identify:

- Whether a system is fully patched
- Whether known vulnerabilities apply
- Whether systems meet organizational security requirements

### Asset Inventory

Security programs depend on accurate inventory information to identify:

- Unsupported operating systems
- Aging hardware
- Unmanaged devices

### Security Baseline Validation

Information returned by `Get-ComputerInfo` can be used to verify system configurations and establish known-good baselines.

---

## 4. Security Scenario

A workstation is suspected of running an outdated version of Windows after a critical vulnerability is announced.

Before determining risk, an analyst must identify:

- The operating system edition
- The Windows feature release
- The operating system build number
- The device being investigated

Using the following command:

```powershell
Get-ComputerInfo |
Select-Object WindowsProductName,
              WindowsVersion,
              OsVersion,
              OsBuildNumber,
              CsName
```

an analyst can quickly gather the information needed to compare the system against published vulnerability information and determine whether remediation is necessary.

---

## 5. Key Takeaways

- PowerShell returns structured objects rather than plain text.
- Property prefixes provide useful context about the type of information being displayed.
- `Select-Object` is essential for reducing clutter and focusing on relevant data.
- `Get-Member` is one of the most valuable commands for exploring unfamiliar PowerShell objects.
- Build numbers identify operating system builds, not hardware models.

### Property Prefixes

| Prefix | Meaning |
|----------|----------|
| Windows* | Windows product information |
| Os* | Operating system information |
| Cs* | Computer system and hardware information |
| Bios* | BIOS and firmware information |
| DeviceGuard* | Security-related information |

---

## 6. Interesting Discoveries

### Build Numbers Are Not Hardware Models

Initially, I assumed that `OsVersion` and `OsBuildNumber` represented some form of system model information.

After examining the properties more closely, I learned:

| Property | Meaning |
|-----------|----------|
| WindowsVersion | Windows feature release |
| OsVersion | Technical operating system version |
| OsBuildNumber | Operating system build identifier |
| CsModel | Hardware model |

This distinction is important because operating system information and hardware information are exposed through separate property groups.

### Hardware Information Lives Under `Cs*`

I expected memory information to appear under operating system-related properties. Instead, memory is exposed through:

```powershell
CsTotalPhysicalMemory
```

This reinforced the idea that PowerShell separates hardware information from operating system information.

### Prefixes Simplify Discovery

Rather than scrolling through hundreds of properties, it is more efficient to filter output using property prefixes:

```powershell
Get-ComputerInfo | Select-Object Os*
```

or

```powershell
Get-ComputerInfo | Select-Object Cs*
```

This makes large objects much easier to explore and understand.
