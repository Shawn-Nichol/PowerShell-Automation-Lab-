# 🛡️ Security Audit Function

![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-blue?style=for-the-badge&logo=powershell&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-Reusable%20Investigation%20Tools-orange?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Security%20Auditing-critical?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Security%20Audit%20Function-informational?style=for-the-badge)

---

## 📌 Executive Summary

This challenge focused on building a reusable PowerShell security audit function capable of collecting baseline workstation information. The function automated the collection of process counts, service counts, download inventory counts, and workstation details, returning the information in a structured format suitable for reporting and export.

---

## 🎯 Challenge Scenario

The objective was to create a reusable investigation tool that could quickly gather workstation information and provide a consistent audit report for analysts.

Rather than executing multiple individual commands, the function collects the information automatically and presents it in a structured format.

---

## 🔐 Cybersecurity Application

Security analysts frequently collect baseline information during investigations and audits.

Reusable PowerShell functions help:

- Standardize evidence collection
- Reduce manual effort
- Improve consistency
- Support reporting workflows
- Lay the foundation for security automation

Functions like this can be expanded in future lessons to include event logs, network information, users, services, and additional investigation data.

---

## ✅ Key Takeaways

- Created a reusable PowerShell function.
- Used function parameters to identify the analyst.
- Returned investigation results using PSCustomObject.
- Combined multiple evidence sources into a single tool.
- Exported collected data for reporting purposes.
- Built a reusable security audit utility.

---

## 💻 PowerShell Commands

### Security Audit Function

```powershell
function Get-SecurityAudit {

    Param(
        $Name
    )

    [PSCustomObject]@{
        AnalystName = $Name
        ComputerName = $env:COMPUTERNAME
        Services = (Get-Service).Count
        Processes = (Get-Process).Count
        Downloads = (Get-ChildItem "$env:USERPROFILE\Downloads").Count
    }
}
```

<img width="661" height="244" alt="image" src="https://github.com/user-attachments/assets/2d4be951-9594-416f-aa11-afd58bb7ff96" />


---

### Execute Security Audit

```powershell
Get-SecurityAudit -Name "Shawn"
```

Output:

```text
AnalystName  : Shawn
ComputerName : ###########
Services     : 323
Processes    : 362
Downloads    : 200
```

<img width="598" height="19" alt="image" src="https://github.com/user-attachments/assets/6363e683-3726-4d9a-ab76-ab6b01c9031e" />


---

### Export Results

```powershell
$ComputerInfo |
    Export-Csv "$Home\Downloads\Summary.csv" -NoTypeInformation
```

<img width="600" height="32" alt="image" src="https://github.com/user-attachments/assets/c32be348-7526-496b-8a40-d6f047a60e9b" />


---

## 🧠 What I Learned

- Built a reusable PowerShell security audit tool.
- Used a parameter to personalize audit results.
- Collected evidence from multiple system sources.
- Returned structured data using PSCustomObject.
- Combined previous PowerShell concepts into a practical security utility.
- Exported investigation data for future review.

---

## 🔍 Investigation Notes

### Security Audit Results

<img width="336" height="106" alt="image" src="https://github.com/user-attachments/assets/7a0a64bc-51a2-49fb-aa8c-81084915200b" />


The function successfully collected workstation information and returned it as a reusable PowerShell object.

---

### Evidence Sources Collected

The audit gathered:

- Computer Name
- Running Process Count
- Service Count
- Downloads Folder Inventory

This information provides a basic workstation baseline that can be used during future investigations.

---

### Export Verification

The audit report was successfully exported to:

```text
Summary.csv
```

This demonstrates how structured investigation results can be preserved and shared.

---

## 🧠 Analyst Reflection

This challenge demonstrated how PowerShell functions can be transformed into practical cybersecurity tools.

Instead of running multiple commands manually, the security audit function provides a repeatable and consistent method of gathering evidence from a workstation.

The ability to collect, organize, and export information through a single function is a foundational automation skill for SOC analysts, incident responders, and system administrators.

Building reusable tools not only saves time but also improves the consistency and quality of investigation results.
