# 🛡️ Collections & Data Processing in PowerShell


[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Large%20Dataset%20Analysis-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Process%20Analysis-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Collections%20%26%20Filtering-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This lesson introduced collections and data processing techniques in PowerShell. By working with collections of objects, analysts can count, sort, filter, and analyze large datasets more efficiently. These skills are essential for reviewing processes, identifying anomalies, and supporting security investigations.


## 🎯 Learning Objective

Learn how to work with collections of objects by counting, sorting, selecting, and filtering data using PowerShell.


## 🔐 Cybersecurity Application

Security analysts frequently work with large collections of data including running processes, services, user accounts, event logs, and network connections. PowerShell allows this information to be collected and processed quickly, helping analysts identify suspicious activity and prioritize investigative efforts.


## ✅ Key Takeaways

- Many PowerShell commands return collections of objects.
- Collections can be stored in variables for analysis.
- The `.Count` property returns the number of objects in a collection.
- `Sort-Object` organizes data based on a selected property.
- `Where-Object` filters data to isolate relevant information.
- Understanding collections is critical for threat hunting and incident response activities.


## 💻 PowerShell Commands

### Counting Objects in a Collection

```powershell
(Get-Process).Count
```

<img width="425" height="99" alt="image" src="https://github.com/user-attachments/assets/5e55e834-f485-412e-9bbf-1ce2aea1f6e4" />


```powershell
$processes = Get-Process

$processes.Count
```

<img width="478" height="110" alt="image" src="https://github.com/user-attachments/assets/2e0472e5-716c-46cb-99a7-fc2bb0d1bb77" />

---

### Selecting Relevant Properties

```powershell
Get-Process |
    Select-Object Name, Id
```

<img width="487" height="195" alt="image" src="https://github.com/user-attachments/assets/ab135201-8fe8-4a0a-a144-0f24925a8ab6" />

---

### Sorting Processes by Memory Usage

```powershell
Get-Process |
    Sort-Object WorkingSet -Descending |
    Select-Object -First 5 Name, WorkingSet
```

SCREENSHOT_HERE

### Filtering a Collection

```powershell
Get-Process |
    Where-Object Name -like "*chrome*"
```

<img width="596" height="352" alt="image" src="https://github.com/user-attachments/assets/7aae2dbf-03a5-4faa-b602-c88bea7ad674" />



## 🧠 What I Learned

- Learned that many PowerShell commands return collections of objects.
- Practiced counting objects using the `.Count` property.
- Used `Select-Object` to display only relevant information.
- Sorted collections using `Sort-Object`.
- Filtered collections using `Where-Object`.
- Gained an understanding of how large datasets can be processed and analyzed during cybersecurity investigations.

