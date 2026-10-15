# 🛡️ Returning Data from Functions

[![PowerShell 7+](https://img.shields.io/badge/PowerShell-7%2B-blue?style=flat-square&logo=powershell&logoColor=white)](https://github.com/PowerShell/PowerShell)
[![Difficulty: Beginner](https://img.shields.io/badge/Difficulty-Beginner-green?style=flat-square)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category: Reusable Investigation Tools](https://img.shields.io/badge/Category-Reusable%20Investigation%20Tools-informational?style=flat-square)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security: Automation](https://img.shields.io/badge/Security-Automation-orange?style=flat-square)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept: Returning Data](https://img.shields.io/badge/Concept-Returning%20Data-purple?style=flat-square)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

---

## 📌 Executive Summary

This lesson introduced the concept of returning data from PowerShell functions. While `Write-Host` displays information directly to the screen, returned data can be stored, reused, exported, and incorporated into larger automation workflows. Understanding this distinction is essential when building reusable cybersecurity investigation tools.

---

## 🎯 Learning Objective

Learn the difference between displaying information and returning information from PowerShell functions.

---

## 🔐 Cybersecurity Application

Security analysts frequently collect evidence and pass investigation results through multiple stages of analysis and reporting.

Returning data allows evidence to be:

- Stored in variables
- Exported to CSV reports
- Included in investigation summaries
- Passed between functions
- Used in automation workflows

Without returned data, investigation findings become much harder to reuse.

---

## ✅ Key Takeaways

- Functions can display information or return information.
- `Write-Host` displays information directly to the screen.
- Returned values can be stored in variables.
- Returned objects can be exported and reported on.
- PSCustomObjects are commonly returned during investigations.
- Returning data supports automation and evidence collection.

---

## 💻 PowerShell Commands

### Displaying Information

```powershell
function Get-Greeting {
    Write-Host "Hello Shawn"
}
```

Run:

```powershell
Get-Greeting
```

Output:

```text
Hello Shawn
```
<img width="306" height="111" alt="image" src="https://github.com/user-attachments/assets/c1dbdecb-f2d1-4cef-b4eb-2bbdcd0dcd55" />



---

### Returning the Computer Name

```powershell
function Get-ComputerName {
    $env:COMPUTERNAME
}
```

Run:

```powershell
Get-ComputerName
```

Output:

```text
###########
```

<img width="329" height="131" alt="image" src="https://github.com/user-attachments/assets/9c1052b7-e7fa-4868-86f4-7220992beb80" />


---

### Service Count

```powershell
$Services = (Get-Service).Count
```

Run:

```powershell
$Services
```

Output:

```text
323
```

<img width="385" height="31" alt="image" src="https://github.com/user-attachments/assets/e9cf0435-3a16-4e28-837e-ca2b849aa3a2" />
<img width="193" height="36" alt="image" src="https://github.com/user-attachments/assets/92dffe6c-dd6d-46b5-bc70-088e52709070" />


---

### Returning a Workstation Summary

```powershell
function Get-WorkstationSummary {

    [PSCustomObject]@{
        Computer  = $env:COMPUTERNAME
        Processes = (Get-Process).Count
        Services  = (Get-Service).Count
    }

}
```

Store the result:

```powershell
$WorkstationInfo = Get-WorkstationSummary
```

Display the result:

```powershell
$WorkstationInfo
```

Output:

```text
Computer     Processes Services
--------     --------- --------
###########       328      323
```

<img width="412" height="133" alt="image" src="https://github.com/user-attachments/assets/9a397633-9c41-4d3f-8a00-bb846bf5320a" />

<img width="301" height="62" alt="image" src="https://github.com/user-attachments/assets/cadd65e0-f96b-4807-9985-36556f3649bb" />


---

## 🧠 What I Learned

- Learned the difference between displaying data and returning data.
- Practiced creating functions that return useful information.
- Stored returned data in variables.
- Used PSCustomObjects within functions.
- Learned how returned data supports automation and reporting.
- Gained an understanding of why investigation functions should return reusable data whenever possible.

---

## 🔍 Investigation Notes

### Computer Name Function

Successfully created a function that returned the workstation hostname:

```text
###########
```

Because the value was returned rather than displayed, it could be stored and reused elsewhere in a script.

---

### Service Count

Collected and stored a service count of:

```text
323
```

This demonstrated how returned values can be assigned to variables and reused later.

---

### Workstation Summary Function

Created a reusable function that returned a structured report containing:

```text
Computer Name
Process Count
Service Count
```

Results:

```text
Computer : ###########
Processes : 328
Services : 323
```

The returned PSCustomObject was successfully stored in a variable and displayed on demand.

---

## 🧠 Analyst Reflection

One of the most important lessons in PowerShell automation is understanding the difference between displaying information and returning information.

Using:

```powershell
Write-Host
```

is useful for showing information on the screen.

Returning data is significantly more powerful because the output can be:

- Stored in variables
- Filtered
- Exported
- Reported on
- Passed to other functions

This makes returned objects far more valuable when building reusable cybersecurity investigation tools and automation workflows.
