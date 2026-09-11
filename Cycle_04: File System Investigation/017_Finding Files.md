# 🛡️ Finding Files in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Filesystem%20Investigation-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-File%20Hunting-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-File%20Discovery-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson focused on locating files within the Windows filesystem using PowerShell. By searching for specific file types and reviewing file inventories, it becomes possible to quickly identify artifacts that may be relevant during a cybersecurity investigation.


## 🎯 Learning Objective

Learn how to search for files using `Get-ChildItem`, the `-Filter` parameter, and recursive searches through subdirectories.

## 🔐 Cybersecurity Application

Security analysts frequently search for specific file types during investigations. Common examples include executables, PowerShell scripts, archives, and configuration files. Quickly locating these files helps establish timelines, identify suspicious artifacts, and collect evidence.


## ✅ Key Takeaways

- `Get-ChildItem` can be used to search for files.
- The `-Filter` parameter narrows search results.
- Recursive searches include subfolders.
- File inventories help establish investigation baselines.
- File hunting is an essential incident response and threat-hunting skill.
- Reviewing file names and dates can reveal unusual activity.

---

## 💻 PowerShell Commands

### Search for MP3 Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Filter "*.mp3"
```

<img width="747" height="377" alt="image" src="https://github.com/user-attachments/assets/1e8bd409-d740-44dc-a016-c603100a7fd9" />


### Search for ZIP Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Filter "*.zip"
```

<img width="838" height="300" alt="image" src="https://github.com/user-attachments/assets/c1576575-9e7d-4300-840f-67a05d7b8a45" />


### Search for CSV Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Filter "*.csv"
```

<img width="745" height="211" alt="image" src="https://github.com/user-attachments/assets/d6657881-b283-452f-8a07-fc251e62dcb5" />


### Search for Executable Files Recursively

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Filter "*.exe" -Recurse
```

<img width="787" height="251" alt="image" src="https://github.com/user-attachments/assets/cfe5dccb-20f4-49fa-95e0-5c5a88c8ef42" />


---

## 🧠 Wha* I Learned

- Learned how to search for files by extension.
- Practiced using the `-Filter` parameter to narrow results.
- Used recursive searches to include subfolders.
- Reviewed file inventories to identify patterns and anomalies.
- Gained experience applying file hunting techniques to a cybersecurity investigation scenario.

---

## 🔍 Investigation Notes

### MP3 File Review

```text
16 MP3 files found
```

Observations:

- Most files followed a*similar naming convention.
- The f*les appeared to originate from an audio logging system.
- No unusual file names were identified.

### ZIP File Review

```text
9 ZIP files found
```

Observations:

- The newest ZIP file was dated August 8, 2026.
- No suspicious archive names were observed during the review.

### CSV File Review

```text
5 CSV files found
```

Examples included:

```text
Telnet Password
WideOrbit Checklist
```

Observations:

- Some filenames suggested configuration or operational information.
- Files referencing passwords would warrant additional review in a real investigation.

### Executable File Review

```text
27 EXE files found
```
Observations:

- No file names appeared suspicious.
- No executable files older than 2026 were identified.
- The Downloads folder may have been cleaned or reorganized at some point.

---

## 🧠 Analyst Reflection

The purpose of file hunting is not simply to count files but to understand what is normal for a system.

During this investigation I focused on:

- File types present in the Downloads directory.
- Naming conventions.
- File age.
- Potentially sensitive artifacts.

No obvious anomalies were identified, but the exercise demonstrated how PowerShell can quickly locate evidence that may require further investigation.

