# 🛡️ Files and Folders in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Filesystem%20Investigation-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-File%20Discovery-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Files%20%26%20Folders-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This lesson introduced files and folders in PowerShell and how they can be investigated using the filesystem. By using `Get-ChildItem`, it is possible to inventory files and directories, review metadata, and begin identifying potentially suspicious artifacts during an investigation.

---

## 🎯 Learning Objective

Learn how to view files and folders, store filesystem information in variables, count objects, and review important file properties.

---

## 🔐 Cybersecurity Application

Files are one of the primary sources of evidence during security investigations. Analysts frequently inventory directories, review recently modified files, identify suspicious file types, and search for unexpected artifacts that may indicate malicious activity.

---

## ✅ Key Takeaways

- `Get-ChildItem` displays files and folders.
- Files and directories can be stored in variables for analysis.
- The `.Count` property returns the number of objects in a collection.
- `Length` displays file size information.
- `LastWriteTime` shows when a file was last modified.
- Filesystem inventory is often the first step in a forensic investigation.

---

## 💻 PowerShell Commands

### Inventory the Current Directory

```powershell
Get-ChildItem
```
<img width="595" height="239" alt="image" src="https://github.com/user-attachments/assets/712cab31-43ce-4a8d-9516-2b4f7824ff97" />

---

### Store Directory Contents

```powershell
$items = Get-ChildItem
```

<img width="412" height="60" alt="image" src="https://github.com/user-attachments/assets/80bacd3e-8954-419b-8d57-b678ee3c512f" />

---

### Count Files and Folders

```powershell
$items.Count
```

SCREENSHOT_HERE

### Display Useful File Properties

```powershell
Get-ChildItem |
    Select-Object Name, Length, LastWriteTime
```

<img width="836" height="210" alt="image" src="https://github.com/user-attachments/assets/c3274f56-de3c-49d6-befb-b3c771c3da7f" />

---

### Review Downloads Folder

```powershell
$downloads = Get-ChildItem "$env:USERPROFILE\Downloads"

$downloads.Count
```

<img width="675" height="81" alt="image" src="https://github.com/user-attachments/assets/f34636a7-8de1-4ecf-b732-df00c6724920" />




## 🧠 What I Learned

- Learned how to inventory files and folders using `Get-ChildItem`.
- Practiced storing filesystem objects in variables.
- Used the `.Count` property to determine the number of items in a directory.
- Learned that the `Length` property displays file size information.
- Used `LastWriteTime` to identify when files were last modified.
- Gained an understanding of how filesystem data can support cybersecurity investigations.


