# 🛡️ Functions Introduction in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Reusable%20Investigation%20Tools-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Automation-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Functions-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced PowerShell functions and demonstrated how frequently used commands can be grouped into reusable tools. Functions allow analysts to reduce repetitive tasks and build investigation utilities that can be executed with a single command.


## 🎯 Learning Objective

Learn how to create PowerShell functions and use them to automate evidence collection tasks.


## 🔐 Cybersecurity Application

Security analysts often execute the same investigative tasks repeatedly. Functions provide a way to package multiple commands into a reusable tool that can quickly collect and present evidence.

Common uses include:

- System summaries
- Process inventories
- Service reviews
- File audits
- Investigation reporting


## ✅ Key Takeaways

- Functions create reusable blocks of PowerShell code.
- Functions reduce repetitive typing.
- Functions can return data and objects.
- Functions support automation and reporting.
- PSCustomObjects can be returned from functions.
- Reusable tools improve investigation efficiency.


## 💻 PowerShell Commands

### Create a System Summary Function

```powershell
function Get-SystemSummary {
    [PSCustomObject]@{
        Computer = $env:COMPUTERNAME
        Processes = (Get-Process).Count
        Services = (Get-Service).Count
    }
}
```

<img width="399" height="117" alt="image" src="https://github.com/user-attachments/assets/fdd03abb-266d-4ad2-90fe-85ad1d094efd" />

---

### Run the Function

```powershell
Get-SystemSummary
```

<img width="223" height="21" alt="image" src="https://github.com/user-attachments/assets/ea97add7-8b45-4732-824d-f5029768f3a3" />
<img width="339" height="52" alt="image" src="https://github.com/user-attachments/assets/fa73678f-827b-4566-8dd7-51c39658fc3e" />


---

## 🧠 What I Learned

- Learned how to create PowerShell functions.
- Practiced grouping multiple commands into a reusable tool.
- Used PSCustomObject inside a function.
- Created a simple evidence collection utility.
- Gained an understanding of how functions support security automation and reporting.

---

## 🔍 Investigation Notes

### System Summary Report

```text
Computer : ##########
Processes: 314
Services : 321
```

Observations:

- The function successfully collected evidence from multiple sources.
- The output was returned as a structured object.
- The same evidence can now be collected repeatedly using a single command.

---

## 🧠 Analyst Reflection

Functions are an important step toward automation because they allow frequently used investigation commands to be reused without rewriting them.

Instead of repeatedly entering multiple commands, a function can collect evidence and return a structured report with a single command:

```powershell
Get-SystemSummary
```

This approach improves consistency and helps build reusable investigation tools.
