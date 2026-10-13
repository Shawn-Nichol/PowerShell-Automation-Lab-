# 🛡️ Function Parameters in PowerShell

[![PowerShell 7+](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-) [![Difficulty Beginner](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-) [![Category Reusable Investigation Tools](https://img.shields.io/badge/Category-Reusable%20Investigation%20Tools-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-) [![Security Automation](https://img.shields.io/badge/Security-Automation-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-) [![Concept Function Parameters](https://img.shields.io/badge/Concept-Function%20Parameters-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced PowerShell function parameters and demonstrated how user input can be passed into reusable functions. Parameters allow a single function to investigate different targets without modifying the underlying code.

---

## 🎯 Learning Objective

Learn how to use parameters within PowerShell functions to create flexible and reusable investigation tools.

---

## 🔐 Cybersecurity Application

Security analysts rarely investigate the same object repeatedly. Parameters allow a single function to review multiple services, processes, files, or users without rewriting code.

Examples include:

- Service investigations
- Process reviews
- File analysis
- User audits
- Threat hunting workflows

---

## ✅ Key Takeaways

- Parameters provide input to functions.
- The `Param()` block defines function parameters.
- Functions become more reusable when parameters are used.
- Parameters reduce hardcoded values.
- PowerShell functions can accept user-supplied investigation targets.
- Functions and parameters are foundational automation skills.

---

## 💻 PowerShell Commands

### Greeting Function

```powershell
function Get-Greeting {

    Param(
        $Name
    )

    "Hello $Name"
}
```

Example:

```powershell
Get-Greeting -Name Shawn
```

Output:

```text
Hello Shawn
```

<img width="374" height="189" alt="image" src="https://github.com/user-attachments/assets/98f2053b-c496-4485-a9ca-00a208140713" />


---

### Service Investigation Function

```powershell
function Get-ServiceStatus {

    Param(
        $Name
    )

    Get-Service $Name
}
```

Example:

```powershell
Get-ServiceStatus -Name WinRM
```

<img width="684" height="244" alt="image" src="https://github.com/user-attachments/assets/a529d82f-7cd5-4204-9e99-b596ce6967a0" />


---

### Process Investigation Function

```powershell
function Get-ProcessInfo {

    Param(
        $Name
    )

    Get-Process -Name $Name
}
```

Example:

```powershell
Get-ProcessInfo -Name explorer
```

<img width="614" height="244" alt="image" src="https://github.com/user-attachments/assets/0633193e-52eb-4a34-a654-92ac1fb0af26" />


---

### Investigation Summary Function

```powershell
function Get-InvestigationSummary {

    Param(
        $Target
    )

    [PSCustomObject]@{
        Analyst      = "Shawn"
        TargetService = $Target
    }
}
```

Example:

```powershell
Get-InvestigationSummary -Target WinRM
```

<img width="501" height="327" alt="image" src="https://github.com/user-attachments/assets/5edfc38c-23d1-48c3-af2f-1072b8500b8a" />


---

## 🧠 What I Learned

- Learned how to create function parameters using `Param()`.
- Practiced accepting user input within functions.
- Used parameters to investigate different services and processes.
- Returned PSCustomObjects from reusable functions.
- Reduced the need for hardcoded values.
- Gained an understanding of how parameters improve automation.

---

## 🔍 Investigation Notes

### Service Review

The service investigation function successfully returned information about:

```text
WinRM
```

including:

```text
Status
Service Name
Display Name
```

---

### Process Review

The process investigation function successfully returned information about:

```text
explorer
```

including:

```text
Process ID
Memory Usage
CPU Usage
```

---

### Investigation Summary

A PSCustomObject was returned using a parameterized function.

Example output:

```text
Analyst : Shawn
TargetService : WinRM
```

This demonstrated how structured investigation reports can be generated dynamically based on user input.

---

## 🧠 Analyst Reflection

Functions become significantly more valuable when parameters are introduced.

Without parameters:

```powershell
Get-WinRM
```

only investigates one service.

With parameters:

```powershell
Get-ServiceStatus -Name WinRM
```

or

```powershell
Get-ServiceStatus -Name BITS
```

the same function can investigate many services without modification.

This improves flexibility and reduces duplicate code.
