# 🛡️ File Filtering in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Filesystem%20Investigation-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-File%20Triage-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-File%20Filtering-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This lesson focused on filtering files to identify the most relevant artifacts during a filesystem investigation. By sorting files by size and modification date, and filtering executables, PowerShell can quickly reduce large file inventories into manageable sets for review.


## 🎯 Learning Objective

Learn how to filter, sort, and prioritize files using PowerShell based on attributes such as size, file type, and modification date.


## 🔐 Cybersecurity Application

Security analysts rarely review every file individually. Instead, they focus on files that stand out based on characteristics such as:

- Large file size
- Recent modification date
- Executable extensions
- Hidden attributes
- Unusual locations

These techniques help analysts identify suspicious artifacts more efficiently during investigations.


## ✅ Key Takeaways

- `Where-Object` can filter files based on properties.
- `Sort-Object` can prioritize results by size or date.
- The `Length` property contains file size information.
- The `LastWriteTime` property contains modification timestamps.
- Large files and recent files are often useful investigation starting points.
- File filtering reduces noise during security investigations.


## 💻 PowerShell Commands

### Find the Largest Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" |
    Sort-Object Length -Descending |
    Select-Object -First 5 Name, Length
```

<img width="628" height="182" alt="image" src="https://github.com/user-attachments/assets/da88579b-4d80-41c9-b4d7-807cd58e0224" />

---

### Find the Most Recently Modified Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" |
    Sort-Object LastWriteTime -Descending |
    Select-Object -First 5 Name, LastWriteTime
```

<img width="715" height="227" alt="image" src="https://github.com/user-attachments/assets/a7dbc7f3-735a-4e99-b89d-529d16972e66" />

---

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Recurse |
    Where-Object Extension -eq ".exe" |
    Sort-Object Length -Descending |
    Select-Object -First 5 Name, Length
```

<img width="517" height="212" alt="image" src="https://github.com/user-attachments/assets/723eb0c9-2930-49de-ac91-f1b5543ecd33" />

---

### Find Files Larger Than 100 MB

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" |
    Where-Object Length -gt 100MB
```

<img width="928" height="304" alt="image" src="https://github.com/user-attachments/assets/17b3545d-d694-499b-a474-c9fe220fd3d9" />


---

## 🧠 What I Learned

- Learned how to prioritize files using sorting and filtering techniques.
- Practiced identifying large files and recently modified files.
- Used the `Length` property to review file sizes.
- Used the `LastWriteTime` property to review modification dates.
- Applied filtering techniques to executable files.
- Gained an understanding of how analysts reduce large data sets into focused investigation targets.
