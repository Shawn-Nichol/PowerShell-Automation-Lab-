# 🛡️ Formatting Investigation Reports in PowerShell

[![PowerShell 7+](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty Beginner](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category Evidence Reporting](https://img.shields.io/badge/Category-Evidence%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security Investigation Reporting](https://img.shields.io/badge/Security-Investigation%20Reporting-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept Format Table & Format List](https://img.shields.io/badge/Concept-Format%20Table%20%26%20Format%20List-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)


## 📌 Executive Summary

This lesson introduced PowerShell formatting cmdlets and demonstrated how investigation results can be displayed in a more readable format. By using `Format-Table` and `Format-List`, analysts can improve the presentation of evidence and make reports easier for other team members and stakeholders to review.


## 🎯 Learning Objective

Learn how to format PowerShell output using `Format-Table` and `Format-List` and understand when each format is appropriate during an investigation.

## 🔐 Cybersecurity Application

Collecting evidence is only part of the investigation process. Security analysts must also communicate findings clearly.

Formatting tools help analysts:

- Create readable investigation summaries.
- Present findings to leadership.
- Review evidence more efficiently.
- Reduce unnecessary information.
- Improve the quality of security reports.


## ✅ Key Takeaways

- `Format-Table` displays information in columns.
- `Format-List` displays information vertically as property/value pairs.
- Tables are best for comparing multiple objects.
- Lists are best for reviewing a single object in detail.
- Proper formatting improves communication during investigations.
- PowerShell formatting helps transform raw data into analyst-friendly reports.


## 💻 PowerShell Commands

### Process Report

```powershell
Get-Process |
    Select-Object ProcessName, Id |
    Format-Table -AutoSize
```

<img width="460" height="344" alt="image" src="https://github.com/user-attachments/assets/bbf6f04c-bc00-4c2f-a43d-5dfac843194e" />

---

### Service Report

```powershell
Get-Service |
    Select-Object Name, Status |
    Format-Table -AutoSize
```

<img width="394" height="202" alt="image" src="https://github.com/user-attachments/assets/3d835ef4-cba4-4a37-9903-6c1c240aa440" />

---

### Filesystem Summary

```powershell
[PSCustomObject]@{
    TotalFiles = 175
    Executables = 27
    HiddenFiles = 9
} | Format-List
```

<img width="269" height="208" alt="image" src="https://github.com/user-attachments/assets/e2de2690-122f-4764-9af2-51b41d2f9384" />


### Investigation Summary

```powershell
[PSCustomObject]@{
    LargestFile = "Windows.iso"
    TotalFiles = 175
    Executables = 27
    Assessment = "No suspicious artifacts identified"
} | Format-List
```

<img width="487" height="207" alt="image" src="https://github.com/user-attachments/assets/f3a7cc8e-5601-4c5e-8277-4a2842b1784e" />


---

## 🧠 What I Learned

- Learned how to display PowerShell output using different formatting methods.
- Practiced using `Format-Table` to compare multiple objects.
- Practiced using `Format-List` to review a single object in detail.
- Learned how formatting improves readability and reporting.
- Gained an understanding of how security analysts present investigation results.

## 🔍 Investigation Notes

### Process Report

A process inventory was displayed using:

```powershell
Format-Table
```

The report focused on:

```text
Process Name
Process ID
```

Observation:

- The output appeared similar to normal PowerShell output because PowerShell automatically uses table-style displays for many collections.
- Using `Format-Table` explicitly provides greater control over report presentation.

### Service Report

A service inventory was displayed using:

```powershell
Format-Table -AutoSize
```

Observation:

- The information contained the same data as the standard output.
- Column spacing was adjusted to improve readability.
- This formatting becomes more valuable when dealing with larger data sets.


### Filesystem Summary

A custom object was formatted using:

```powershell
Format-List
```

Observation:

- The vertical layout made it easier to read individual properties.
- Information was clearly separated and easy to interpret.
