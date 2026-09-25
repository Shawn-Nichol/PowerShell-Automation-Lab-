# 🛡️ Evidence Collection Basics in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Evidence%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Evidence%20Collection-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Investigation%20Workflow-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This lesson introduced evidence collection fundamentals and the role evidence plays during cybersecurity investigations. Rather than drawing conclusions based on assumptions, analysts collect, preserve, and review evidence before developing findings and recommendations.

---

## 🎯 Learning Objective

Learn what constitutes evidence, identify common evidence sources, and create structured summaries of collected information using PowerShell.

---

## 🔐 Cybersecurity Application

Evidence collection is one of the first responsibilities of a SOC analyst or incident responder.

Common evidence sources include:

- Running processes
- Running services
- Files and directories
- System information
- User accounts
- Network activity

Collecting evidence before making conclusions helps ensure investigations are based on facts rather than assumptions.

---

## ✅ Key Takeaways

- Evidence helps answer investigative questions.
- Evidence should be collected before conclusions are made.
- Structured evidence is easier to preserve and report.
- PowerShell provides access to many important evidence sources.
- Evidence collection should be repeatable and documented.
- Good investigations are based on observations rather than guesses.

---

## 💻 PowerShell Commands

### Collect Process Count

```powershell
(Get-Process).Count
```

<img width="358" height="60" alt="image" src="https://github.com/user-attachments/assets/57ba2534-b722-4ec8-8687-086fe50d67c0" />


### Collect Service Count

```powershell
(Get-Service).Count
```

<img width="238" height="81" alt="image" src="https://github.com/user-attachments/assets/a6dee117-57b0-4ce2-a7e7-b5461f31d483" />


### Collect Downloads Inventory Count

```powershell
(Get-ChildItem "$env:USERPROFILE\Downloads").Count
```

<img width="598" height="78" alt="image" src="https://github.com/user-attachments/assets/c200e914-1e2b-4743-b3df-d52c7de1ac5f" />


### Create Evidence Summary

```powershell
[PSCustomObject]@{
    ComputerName = $env:COMPUTERNAME
    ProcessCount = (Get-Process).Count
    ServiceCount = (Get-Service).Count
    DownloadFiles = (Get-ChildItem "$env:USERPROFILE\Downloads").Count
}
```

<img width="647" height="104" alt="image" src="https://github.com/user-attachments/assets/e83e83c9-b3c6-4911-ab6f-1243a36df308" />
<img width="463" height="138" alt="image" src="https://github.com/user-attachments/assets/ed788afb-c606-4319-bee8-071ae9ce7714" />


### Display Evidence Summary

```powershell
$report | Format-List
```
<img width="362" height="114" alt="image" src="https://github.com/user-attachments/assets/5bc3486f-9967-41b7-af95-7294e42de1bb" />


---

## 🧠 What I Learned

- Learned what constitutes evidence during an investigation.
- Practiced collecting evidence from multiple sources.
- Created a structured evidence summary using PSCustomObject.
- Reinforced the importance of evidence-based analysis.
- Gained a better understanding of investigative workflows.


## 🔍 Investigation Notes

### Evidence Summary

```text
Computer Name : ##########
Process Count : 334
Service Count : 321
Downloads Files : 181
```

### Collection Notes

During service collection, two Windows services generated access-related warnings:

```text
IsolationSession
WaaSMedicSvc
```

The warnings did not affect overall evidence collection, and service counts were still successfully collected.


## 🧠 Analyst Reflection

A key lesson from this exercise is that evidence should always be collected before conclusions are made.

A poor investigation approach is:

```text
Assume
Analyze
Conclude
```

A professional investigation approach is:

```text
Collect Evidence
Analyze Evidence
Develop Findings
Reach Conclusions
```

Evidence provides the factual foundation needed to support investigative decisions.
