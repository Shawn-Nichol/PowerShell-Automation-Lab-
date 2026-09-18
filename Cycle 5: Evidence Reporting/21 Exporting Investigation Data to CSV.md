# 🛡️ Exporting Data to CSV in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Evidence%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Evidence%20Collection-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-CSV%20Export-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced the `Export-Csv` cmdlet and demonstrated how PowerShell can preserve investigation results in a structured format. Rather than relying on screenshots or console output, CSV files allow analysts to save, share, sort, filter, and revisit findings during future investigations.

---

## 🎯 Learning Objective

Learn how to export PowerShell data to CSV files and understand how exported evidence supports investigation, reporting, and documentation workflows.

---

## 🔐 Cybersecurity Application

Security analysts frequently export evidence collected during investigations. CSV reports can be used to preserve process inventories, file inventories, service audits, user reviews, and other investigative findings.

Exported data can then be:

- Reviewed in Excel
- Shared with other analysts
- Stored as investigation evidence
- Compared with future investigations
- Included in incident response documentation

---

## ✅ Key Takeaways

- `Export-Csv` saves PowerShell output to a CSV file.
- CSV files preserve investigation results for future review.
- `Select-Object` can be used to export only relevant information.
- The `-NoTypeInformation` parameter removes unnecessary metadata.
- CSV files can be opened in Excel and other reporting tools.
- Structured evidence is more useful than screenshots during investigations.

---

## 💻 PowerShell Commands

### Export a Process Inventory

```powershell
Get-Process |
    Select-Object ProcessName, Id |
    Export-Csv "$env:USERPROFILE\Desktop\ProcessInventory.csv" -NoTypeInformation
```

<img width="872" height="226" alt="image" src="https://github.com/user-attachments/assets/ae2a1952-6098-43ca-9111-469e7148dde9" />


### Export a Downloads Inventory

---

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" |
    Select-Object Name, Length, LastWriteTime |
    Export-Csv "$env:USERPROFILE\Desktop\DownloadsInventory.csv" -NoTypeInformation
```

<img width="850" height="218" alt="image" src="https://github.com/user-attachments/assets/ceecc622-1b89-4d87-b6b7-11048f0a4d63" />

---

### Export Executable Files

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" |
    Where-Object Extension -eq ".exe" |
    Select-Object Name, Length, LastWriteTime |
    Export-Csv "$env:USERPROFILE\Desktop\Executables.csv" -NoTypeInformation
```

<img width="852" height="236" alt="image" src="https://github.com/user-attachments/assets/db1fbbe2-31e5-4588-8851-b38c5fb06fba" />


---

## 🧠 What I Learned

- Learned how to export PowerShell data into CSV files.
- Practiced selecting only relevant properties before exporting.
- Learned how to remove PowerShell type information using `-NoTypeInformation`.
- Gained an understanding of how evidence can be preserved for future review.
- Learned why cybersecurity analysts often export investigation results rather than relying on screenshots.
