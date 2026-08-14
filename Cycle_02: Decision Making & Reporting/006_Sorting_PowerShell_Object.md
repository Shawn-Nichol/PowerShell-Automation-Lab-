# 🛡️ Sorting PowerShell Objects

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Pipeline%20%26%20Sorting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Triage%20%26%20Investigation-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Sort--Object-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)


## 📌 Executive Summary

This lesson introduced object sorting with `Sort-Object`. By sorting process data, I learned how to quickly identify resource-intensive applications and create focused investigation reports.


## 🎯 Learning Objective

Learn how to sort PowerShell objects using object properties and prioritize the most relevant results.


## 🔐 Cybersecurity Application

Sorting allows analysts to rapidly identify unusual behavior such as high CPU consumption, excessive memory usage, or abnormal system activity during investigations.


## ✅ Key Takeaways

- `Sort-Object` sorts PowerShell objects.
- `-Descending` reverses the sort order.
- Sorting can prioritize investigation targets.
- `Select-Object -First` limits output to the most relevant entries.
- Sorting improves report readability.


## 💻 PowerShell Commands

```powershell
Get-Process |
Sort-Object CPU -Descending
```
<img width="891" height="400" alt="image" src="https://github.com/user-attachments/assets/23632fc3-c498-4cfd-a4f0-824477748c9c" />


```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object ProcessName,
              Id,
              CPU
```

<img width="649" height="420" alt="image" src="https://github.com/user-attachments/assets/ee4c5773-4d92-4da3-8011-e84c7101ccf6" />


```powershell
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 5 ProcessName,
                        Id,
                        CPU
```
<img width="434" height="229" alt="image" src="https://github.com/user-attachments/assets/8a0bd585-e066-4ec4-8f01-6fc8c04aad5b" />


## 🧠 What I Learned

- How to sort PowerShell object data.
- How to find high-resource processes quickly.
- How to combine sorting and selection.
- How sorting supports cybersecurity investigations.
