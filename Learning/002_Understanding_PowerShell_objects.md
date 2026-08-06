# 🛡️ Understanding PowerShell Objects

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Objects-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Cybersecurity-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Properties%20and%20Values-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

images/powershell-objects-hero.png

---

## 📌 Executive Summary

This session introduced PowerShell objects and object properties. I learned that PowerShell commands return structured data rather than plain text and that object properties can be inspected and selected for analysis.

---

## 🎯 Learning Objective

Understand how PowerShell stores information in objects and how to access useful properties.

---

## 🚀 Key Highlights

- Used `Get-Member` to inspect object properties.
- Learned the difference between property names and property values.
- Used `Select-Object` to display custom properties.
- Viewed process data through selected properties.

---

## ✅ Key Takeaways

- PowerShell returns objects, not plain text.
- Objects contain properties.
- Get-Member reveals available properties.
- Select-Object displays chosen properties.

## 💻 PowerShell Commands


```powershell
Get-Process |
Get-Member
```
<img width="1356" height="636" alt="image" src="https://github.com/user-attachments/assets/ee6db7f3-b66e-4c39-81cd-8cae58deeddf" />


```powershell
Get-Process |
Get-Member -MemberType Property
```
<img width="828" height="544" alt="image" src="https://github.com/user-attachments/assets/2af4b6fc-bf2c-4abc-ade5-0f6869604ec8" />



```powershell
Get-Process |
Select-Object ProcessName,
              Id,
              Responding -Frist 10
```
<img width="407" height="286" alt="image" src="https://github.com/user-attachments/assets/42c0c983-8a43-4b7d-b6dd-fa2f728f0dfe" />

---

## 🔐 Cybersecurity Application

Analysts rarely need every available property. Using Select-Object allows investigation data to be focused on exactly the fields required for incident response and troubleshooting.
