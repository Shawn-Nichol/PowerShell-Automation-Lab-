# 🛡️ Lesson 015: Process Inventory Audit Challenge

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Large%20Dataset%20Analysis-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Process%20Analysis-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Collections%20%26%20Filtering-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This challenge focused on collecting and analyzing process information from a Windows workstation using PowerShell. The objective was to build a process inventory, identify key system activity, and produce a basic SOC-style investigation summary using the concepts learned throughout the Large Dataset Analysis cycle.


## 🎯 Challenge Scenario

A workstation was flagged for unusual activity and the security team requested a process inventory to establish a baseline of running processes.

As the investigating analyst, I was responsible for:

- Collecting process information.
- Determining the total number of running processes.
- Reviewing process activity.
- Identifying notable findings.
- Producing an investigation summary.


## 🔎 Questions to Answer

### 1. How many processes are currently running?

### 2. Which processes appear most relevant for investigation?

### 3. Is PowerShell currently running on the system?

### 4. What observations should be documented for future investigation?


## 🧠 Investigation Approach

To answer these questions, I:

1. Collected all running processes using `Get-Process`.
2. Stored the results in a variable.
3. Counted the total number of process objects.
4. Attempted to identify high-memory processes through sorting.
5. Searched the process inventory for PowerShell activity.
6. Reviewed findings and documented observations.


## 💻 My Solution

### Collect Process Inventory

```powershell
$process = Get-Process

Write-Host "Total Running Processes:" $process.Count
```
PS C:\> $process = Get-Process
>>
>> Write-Host "Total Running Processes:" $process.Count
Total Running Processes: 362
PS C:\>

### Process Count
```text
Total Running Processes: 366
```

No PowerShell processes were identified during the inventory review.

---

### Search for PowerShell Activity

```powershell
Get-Process |
    Where-Object ProcessName -like "*power*"
```

```powershell
$process |
    Where-Object ProcessName -like "*powershell*"
```
<img width="502" height="116" alt="image" src="https://github.com/user-attachments/assets/de7637ac-84bb-4006-a80b-e7200b96f5d6" />

---

### PowerShell Activity

```text
PowerShell Process Not Found
```

### Memory Analysis

```powershell
$process |
    Sort-Object WorkingSet -Descending |
    Select-Object -First 5 ProcessName, Id, WorkingSet
```
<img width="518" height="263" alt="image" src="https://github.com/user-attachments/assets/d679e45f-dfab-4983-bc0c-5d63a48df40c" />

---

## 🔍 Analyst Assessment

### Observations

- The system contained 366 running processes.
- No active PowerShell process was identified during the investigation.
- A large process inventory may indicate multiple applications, browser instances, system services, and security tools operating simultaneously.
- Additional investigation would be required to determine whether any processes are unusual for the environment.


## 🧠 What I Learned

- Learned how to analyze collections of process objects.
- Used the `.Count` property to establish an inventory baseline.
- Practiced sorting and filtering process information.
- Used `Where-Object` to search for specific processes.
- Applied collection analysis techniques to a cybersecurity investigation scenario.
- Gained an understanding of how process inventories support threat hunting and incident response activities.
