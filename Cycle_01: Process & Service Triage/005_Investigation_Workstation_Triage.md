# 🛡️ Workstation Triage Investigation

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-System%20Triage-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Incident%20Response-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Investigation-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)


## 📌 Executive Summary

This challenge applied the PowerShell skills learned during Learning Cycle 1 to perform a basic workstation triage investigation. The objective was to determine whether a user's complaint of poor system performance was supported by available evidence and to identify any processes or services requiring further review.

Using PowerShell, I analyzed running processes, identified non-responsive applications, reviewed memory consumption, and verified service status without making any changes to the workstation.

## 🎯 Learning Objective

Apply PowerShell fundamentals to perform a structured workstation investigation using:

- Process enumeration
- Property selection
- Filtering
- Sorting
- Service inspection


## 🔐 Cybersecurity Application

Workstation triage is a common activity during incident response and troubleshooting. Analysts use PowerShell to gather system information, identify anomalies, and determine whether additional investigation is required.

This exercise demonstrated how PowerShell can be used to quickly collect evidence while preserving system state.


## ✅ Key Takeaways

- Used PowerShell to investigate system performance concerns.
- Identified non-responsive applications through process filtering.
- Ranked processes by memory consumption.
- Verified the operational state of critical Windows services.
- Practiced documenting findings using an analyst mindset.


## 💻 PowerShell Commands Used

### Identify Non-Responsive Processes

```powershell
Get-Process |
Where-Object Responding -eq $false |
Select-Object ProcessName,
              Id,
              Responding
```

### Find Top Memory Consumers

```powershell
Get-Process |
Select-Object ProcessName,
              Id,
              WorkingSet64 |
Sort-Object WorkingSet64 -Descending |
Select-Object -First 10
```

### Review Running Services

```powershell
Get-Service |
Where-Object Status -eq 'Running' |
Select-Object Name,
              Status |
Select-Object -First 10
```

---

## 🔎 Investigation Findings

### Non-Responding Processes

| Process Name | PID |
|-------------|------|
| SystemSettings | 24296 |

One non-responsive application was identified. The process appeared to be the Windows Settings application.


### Top Memory Consumers

| Process Name | PID | Working Set (Bytes) |
|-------------|------|-------------------:|
| Memory Compression | 3772 | 722,243,584 |
| xagt | 4908 | 718,573,568 |
| chrome | 16468 | 361,959,424 |
| Grammarly.Desktop | 14348 | 358,510,592 |
| msedgewebview2 | 18040 | 346,906,624 |

The highest memory consumers included Windows Memory Compression, the enterprise endpoint security agent (`xagt`), Chrome, Grammarly Desktop, and Microsoft Edge WebView2.


### Running Services Reviewed

| Service Name | Status |
|-------------|---------|
| Appinfo | Running |
| AppXSvc | Running |
| AudioEndpointBuilder | Running |
| Audiosrv | Running |
| Avecto (Privilege Management Service) | Running |

The reviewed services appeared healthy and operational.


## 🧠 Analyst Assessment

The workstation appeared generally healthy during this investigation.

One non-responsive process (`SystemSettings`) was identified, but this alone does not indicate malicious activity or system compromise. The process is associated with a standard Windows component and may have been temporarily unresponsive.

Memory analysis revealed that Windows Memory Compression and the endpoint security agent (`xagt`) were consuming the largest amounts of memory. Both are expected system components and do not immediately suggest suspicious behavior.

Service review confirmed that core Windows and audio-related services were operating normally. No unusual process names, service failures, or obvious indicators of compromise were observed.

Based on the evidence collected, the user's report of reduced performance is plausible; however, no indicators of malicious activity were identified during this initial triage.

---

## 🧠 What I Learned

- How to investigate a workstation using PowerShell without making system changes.
- How to identify non-responsive applications.
- How to sort and analyze processes based on memory usage.
- How to use service status information to assess system health.
- How to document findings in an incident-style report.


## 🚀 Next Step

Begin Learning Cycle 2 by learning how to use variables to store investigation results and reuse collected data during analysis.

Example:

```powershell
$Processes = Get-Process

$Processes |
Where-Object WorkingSet64 -gt 500MB
```

This introduces the foundation of PowerShell automation and repeatable investigations.
