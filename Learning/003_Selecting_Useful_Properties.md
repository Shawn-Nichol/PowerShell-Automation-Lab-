# 🛡️ Selecting Useful Properties

---
[![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B%20%7C%207%2B-5391FE?style=flat&logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Pipeline%20%26%20Properties-blue?style=flat)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Focus](https://img.shields.io/badge/Focus-Select--Object-0078D4?style=flat&logo=powershell)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Application](https://img.shields.io/badge/Application-Cybersecurity%20%26%20Incident%20Response-red?style=flat&logo=shield)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-brightgreen?style=flat)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)


## 📌 Executive Summary

This session focused on using `Select-Object` to display only the properties relevant to an investigation or troubleshooting task. Instead of accepting PowerShell's default view, I learned how to customize output to highlight specific information.

---

## 🎯 Learning Objective

Learn how to use `Select-Object` to extract useful information from PowerShell objects.

---

## 🔐 Cybersecurity Application

Analysts often need only a small subset of available data. Selecting specific properties makes process investigations, service audits, and incident response activities more efficient.

---

## ✅ Key Takeaways

- `Select-Object` controls which properties are displayed.
- Objects contain more information than the default view shows.
- Choosing relevant properties improves readability.
- Process and service data can be tailored for investigations.

---

## 💻 PowerShell Commands

```powershell
Get-Process |
Select-Object ProcessName,
              Id
```
<img width="354" height="336" alt="image" src="https://github.com/user-attachments/assets/bed55691-2d8a-4a1f-b2e0-45a856a61784" />


```powershell
Get-Process |
Select-Object ProcessName,
              Id,
              Responding
```
<img width="395" height="300" alt="image" src="https://github.com/user-attachments/assets/b20e70f4-9e6f-4586-9720-c2b31d0d2427" />

```powershell
Get-Service |
Select-Object Name,
              Status
```
<img width="411" height="285" alt="image" src="https://github.com/user-attachments/assets/70856c32-1996-49c7-b9d0-431876702857" />


```powershell
Get-Process |
Select-Object ProcessName,
              Id,
              WorkingSet64 |
Sort-Object WorkingSet64 -Descending
```
<img width="377" height="321" alt="image" src="https://github.com/user-attachments/assets/33042fc7-3a3e-42e3-a29c-99cf7dfcd013" />

---

## 🧠 What I Learned

- How to select specific properties from PowerShell objects.
- The difference between default output and customized output.
- How to display process and service information efficiently.
- How memory usage can help identify resource-intensive processes.

---
