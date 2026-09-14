# 🛡️ File Attributes in PowerShell

![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)
![Category](https://img.shields.io/badge/Category-Filesystem%20Investigation-blue)
![Security](https://img.shields.io/badge/Security-Hidden%20File%20Analysis-red)
![Concept](https://img.shields.io/badge/Concept-File%20Attributes-orange)
## 📌 Executive Summary

This lesson introduced file attributes and how they can be used during filesystem investigations. By examining attributes such as Hidden, System, and Archive, security analysts can identify files that may not appear during a normal directory review and gain additional context about filesystem activity.

---

## 🎯 Learning Objective

Learn how to view file attributes, identify hidden files, and use PowerShell to display files that may not appear during a standard directory listing.

---

## 🔐 Cybersecurity Application

Threat actors often attempt to conceal files from users by leveraging file attributes such as Hidden and System. During an investigation, analysts should review file attributes to ensure potentially important evidence is not overlooked.

Common uses include:

- Locating hidden files
- Identifying temporary artifacts
- Reviewing system configuration files
- Investigating suspicious filesystem activity
- Establishing a directory baseline

---

## ✅ Key Takeaways

- File attributes provide additional information about files and folders.
- The `Attributes` property displays file attributes.
- `Get-ChildItem -Force` displays hidden items.
- Hidden files do not normally appear in standard directory listings.
- Archive is one of the most common file attributes.
- Hidden and System attributes should always be reviewed during investigations.

---

## 💻 PowerShell Commands

### View File Attributes

```powershell
Get-ChildItem |
    Select-Object Name, Attributes
```

<img width="602" height="380" alt="image" src="https://github.com/user-attachments/assets/ad11d619-85d5-4ed2-89bb-dcb0dd96abf4" />


### Display Hidden Files

```powershell
Get-ChildItem -Force
```

<img width="924" height="361" alt="image" src="https://github.com/user-attachments/assets/bf532a5c-75f2-4cf1-88f2-860ac4628963" />


### Locate Hidden Files

```powershell
Get-ChildItem -Force |
    Where-Object Attributes -like "*Hidden*"
```

<img width="754" height="268" alt="image" src="https://github.com/user-attachments/assets/cf2c710b-6cb3-426d-97c9-bc107d62af1f" />


### Review Downloads Folder Attributes

```powershell
Get-ChildItem "$env:USERPROFILE\Downloads" -Force |
    Select-Object Name, Attributes
```

<img width="1640" height="341" alt="image" src="https://github.com/user-attachments/assets/25dde437-686b-4637-9beb-bc5e5dd168fa" />


---

## 🧠 What I Learned

- Learned how to view file attributes using PowerShell.
- Practiced locating hidden files using `Get-ChildItem -Force`.
- Identified files that would not normally appear during standard directory reviews.
- Learned the difference between Hidden, System, and Archive attributes.
- Gained experience reviewing filesystem metadata during an investigation.


## 🔍 Investigation Notes

### Directory Review

A standard directory listing returned:

```text
164 Items
```

Using:

```powershell
Get-ChildItem -Force
```

returned:

```text
173 Items
```

This revealed:

```text
9 Hidden Items
```

that were not visible during a normal directory review.


### Hidden Files Identified

Several hidden files were discovered, including:

```text
~$ble labels WOA.docx
~$itical Thinking Touchstone 4.docx
~$ndows11_Minimum_Requirement_Check_Commands Nicole Raymaker.docx
~$rformance Through Partnership - F2026 Coaching Guide.docx
```

These appear to be temporary Microsoft Office lock files.

Additional temporary files included:

```text
~WRL0005.tmp
~WRL0284.tmp
~WRL1962.tmp
~WRL3265.tmp
```

These appear to be application-generated temporary files.

---

### Notable Hidden File

```text
desktop.ini
```

Attributes:

```text
Archive
Hidden
System
```

Observations:

- Standard Windows configuration file.
- Hidden from normal directory views.
- No indication of suspicious activity.


### Downloads Folder Review

Observations:

- Most files contained the Archive attribute.
- Hidden files were present.
- No unusual or suspicious attributes were identified.
- Hidden items appeared to be associated with normal operating system and application activity.
