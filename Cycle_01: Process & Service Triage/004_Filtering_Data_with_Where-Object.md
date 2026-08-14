# 🛡️ Filtering Data with Where-Object
[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Pipeline%20%26%20Filtering-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Threat%20Hunting-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Where--Object-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This session introduced PowerShell filtering using `Where-Object`. Instead of reviewing every object returned by a command, I learned how to isolate only the data relevant to an investigation.



## 🎯 Learning Objective

Learn how to filter PowerShell objects based on property values.



## 🔐 Cybersecurity Application

Filtering is essential during investigations because analysts rarely need every result. Using `Where-Object` allows rapid identification of suspicious processes, service states, and system conditions.



## ✅ Key Takeaways

- `Where-Object` filters objects based on property values.
- Comparison operators help define filtering conditions.
- Running and stopped services can be isolated quickly.
- Process investigations often begin by filtering large datasets.



## 💻 PowerShell Commands

```powershell
Get-Service |
Where-Object Status -eq 'Running'
```
<img width="695" height="347" alt="image" src="https://github.com/user-attachments/assets/ff2a9d49-d0d0-4233-bb4c-7ac978c1a2c7" />

```powershell
Get-Service |
Where-Object Status -eq 'Stopped'
```
<img width="621" height="311" alt="image" src="https://github.com/user-attachments/assets/317e4993-d670-4ddd-b285-eac8e3e382c9" />


```powershell
Get-Process |
Where-Object ProcessName -like '*powershell*'
```
<img width="688" height="130" alt="image" src="https://github.com/user-attachments/assets/e512db5f-4e93-4fdb-92cb-8560ba6bdcfc" />


```powershell
Get-Process |
Where-Object Responding -eq $false
```
<img width="685" height="137" alt="image" src="https://github.com/user-attachments/assets/5e4f7f7a-70c4-48f5-bba2-264e78ec44ed" />



## 🧠 What I Learned

- How to filter data instead of reviewing entire outputs.
- How to use comparison operators.
- How to find specific services and processes.
- How filtering supports cybersecurity investigations.


## 🚀 Next Step

Apply command discovery, object inspection, property selection, and filtering together in a cybersecurity investigation challenge.
