# 🛡️ Lesson 025: Security Evidence Report Challenge

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Evidence%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Evidence%20Collection-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Project](https://img.shields.io/badge/Project-Security%20Evidence%20Report-purple)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This challenge focused on collecting and documenting evidence from a Windows workstation using PowerShell. The objective was to gather key system metrics, organize the findings into a structured report, and provide an evidence-based assessment rather than relying on assumptions.

The investigation applied the reporting, formatting, and evidence collection techniques learned throughout the Evidence Reporting cycle.

## 🎯 Challenge Scenario

A workstation was flagged for review after a user reported unusual system behavior.

As the investigating analyst, I was tasked with:

- Collecting baseline system evidence.
- Reviewing process and service inventories.
- Reviewing file inventory data.
- Documenting collection observations.
- Providing an analyst assessment based on collected evidence.


## 🔎 Questions to Answer

### 1. Which computer was investigated?

### 2. How many processes were running?

### 3. How many services were present?

### 4. How many files existed in Downloads?

### 5. Were any collection warnings observed?

### 6. What conclusions could be made from the collected evidence?

---

## 🧠 Investigation Approach

To answer these questions, I:

1. Collected the computer name.
2. Counted running processes.
3. Counted installed services.
4. Counted files within the Downloads directory.
5. Organized the results into a structured report object.
6. Reviewed collection output for warnings.
7. Documented observations and findings.

---

## 💻 My Solution

### Create Evidence Report

```powershell
$report = [PSCustomObject]@{
    ComputerName  = $env:COMPUTERNAME
    ProcessCount  = (Get-Process).Count
    ServiceCount  = (Get-Service).Count
    DownloadFiles = (Get-ChildItem "$env:USERPROFILE\Downloads").Count
}
```

### Display Evidence Report

```powershell
$report | Format-List
```

### Export Evidence Report

```powershell
$report |
    Export-Csv "$env:USERPROFILE\Downloads\Lesson25.csv" -NoTypeInformation
```

---

## 📊 Investigation Results

### Computer Information

```text
Computer Name: ######
```
<img width="739" height="116" alt="image" src="https://github.com/user-attachments/assets/bbf433c2-5570-4be7-b92f-653eb21eb542" />

### Evidence Summary
<img width="354" height="127" alt="image" src="https://github.com/user-attachments/assets/cff38ec9-7a5b-4582-a801-527ca8567f68" />

```text
Process Count: 326
Service Count: 320
Downloaded Files: 181
```

### Report Output

```text
ComputerName  : #######
ProcessCount  : 326
ServiceCount  : 320
DownloadFiles : 181
```
Save report to a CSV file. 
<img width="731" height="51" alt="image" src="https://github.com/user-attachments/assets/56ec28df-dc67-4f82-bf87-95d499cbe983" />

---

## 🔍 Analyst Observations

- Evidence collection completed successfully.
- Process, service, and file inventories were successfully collected.
- Structured evidence was organized into a PowerShell custom object.
- The report was suitable for formatting and export.
- Previous evidence collection activities identified access warnings when querying protected Windows services.

### Collection Notes

During earlier evidence collection activities, the following services generated access-related warnings:

```text
IsolationSession
WaaSMedicSvc
```

These warnings did not prevent evidence collection from completing successfully.

---

## 🧠 Analyst Assessment

```text
No suspicious activity identified during baseline evidence collection.
```

The workstation appears to be operating normally based on the evidence reviewed.

Key observations:

- Service counts appear within expected operating ranges.
- Downloads inventory size appears consistent with routine workstation usage.
- No evidence collected during this exercise indicated suspicious system activity.

Additional investigation would only be warranted if:

- New indicators of compromise (IOCs) are identified.
- A suspicious file or process is reported.
- Additional evidence sources suggest abnormal behavior.


## 🧠 What I Learned

- Applied PowerShell reporting techniques during an investigation.
- Collected evidence from multiple Windows sources.
- Created structured evidence using PSCustomObject.
