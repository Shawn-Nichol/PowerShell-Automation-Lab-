# 🛡️ Reusable Investigation Scripts

![PowerShell 7+](https://img.shields.io/badge/PowerShell-7%2B-blue?logo=powershell&logoColor=white)
![Difficulty: Beginner](https://img.shields.io/badge/Difficulty-Beginner-green)
![Category: Reusable Investigation Tools](https://img.shields.io/badge/Category-Reusable%20Investigation%20Tools-orange)
![Security: Automation](https://img.shields.io/badge/Security-Automation-red?logo=security&logoColor=white)
![Concept: Investigation Scripts](https://img.shields.io/badge/Concept-Investigation%20Scripts-purple)

---

## 📌 Executive Summary

This lesson combined functions, parameters, returned data, and custom objects to create reusable investigation scripts. Rather than repeatedly running individual commands, multiple evidence collection tasks were consolidated into a single function that can be executed whenever needed.

---

## 🎯 Learning Objective

Learn how to combine PowerShell functions and PSCustomObjects into reusable investigation scripts that collect and organize evidence.

---

## 🔐 Cybersecurity Application

Security analysts often perform the same investigations repeatedly across multiple systems. Reusable investigation scripts help standardize evidence collection, reduce mistakes, improve consistency, and support automation efforts.

Common uses include:

- System inventory collection
- Host baselining
- Security audits
- Evidence collection
- Investigation reporting

---

## ✅ Key Takeaways

- Functions can be combined into reusable investigation tools.
- PSCustomObjects provide structured reporting.
- Returned data can be formatted, stored, and exported.
- Investigation scripts reduce repetitive manual work.
- Consistent evidence collection improves investigations.
- Reusable tools are a foundational automation skill.

---

## 💻 PowerShell Commands

### System Summary Function

```powershell
function Get-SystemSummary {
    [PSCustomObject]@{
        Computer  = $env:COMPUTERNAME
        Services  = (Get-Service).Count
        Processes = (Get-Process).Count
        Downloads = (Get-ChildItem "$env:USERPROFILE\Downloads").Count
    }
}
```

<img width="670" height="135" alt="image" src="https://github.com/user-attachments/assets/8e5d1203-5dc1-4b57-b351-9a368d8886a4" />
<img width="377" height="55" alt="image" src="https://github.com/user-attachments/assets/6ac2f3b7-641a-4651-9e73-0269b05d7bbe" />


### Store Results in a Variable

```powershell
$ComputerInfo = Get-SystemSummary
```

<img width="370" height="32" alt="image" src="https://github.com/user-attachments/assets/0a818b2c-e669-4e95-a950-3e97ead5b25f" />
<img width="371" height="87" alt="image" src="https://github.com/user-attachments/assets/6b430a62-2642-4a78-8ffe-05f9ca5a46d1" />


### Display Summary Report

```powershell
$ComputerInfo | Format-List
```

Output:

```text
Computer  : ############
Services  : 323
Processes : 336
Downloads : 199
```

<img width="326" height="108" alt="image" src="https://github.com/user-attachments/assets/41093dba-da17-42f0-a6b4-8789ad9b6dc0" />


---

### Investigation Report Function

```powershell
function Get-InvestigationReport {
    [PSCustomObject]@{
        Computer  = $env:COMPUTERNAME
        Analyst   = "Shawn"
        Processes = (Get-Process).Count
    }
}
```

<img width="462" height="211" alt="image" src="https://github.com/user-attachments/assets/5a2211ca-8f80-448a-b97c-4084d6fe317e" />


### Run Investigation Report

```powershell
Get-InvestigationReport
```

Output:

```text
Computer     Analyst Processes
--------     ------- ---------
########### Shawn         342
```

<img width="462" height="211" alt="image" src="https://github.com/user-attachments/assets/a714ca8e-90df-4f33-8d5f-48979289bdab" />


---

### Export Investigation Results

```powershell
Get-InvestigationReport |
    Export-Csv "$Home\Downloads\Summary.csv" -NoTypeInformation
```

<img width="620" height="35" alt="image" src="https://github.com/user-attachments/assets/d38b3753-0ea1-400c-8555-9d515b84964e" />


---

## 🧠 What I Learned

- Combined multiple PowerShell concepts into a reusable script.
- Used functions to automate evidence collection.
- Returned structured data using PSCustomObjects.
- Stored investigation results in variables.
- Exported report data to CSV.
- Learned how reusable scripts support security investigations and reporting.

---

## 🔍 Investigation Notes

### System Summary Results

The reusable system summary function collected:

```text
Computer  : ############
Services  : 323
Processes : 336
Downloads : 199
```

The function successfully combined multiple evidence sources into a single report.

---

### Investigation Report Results

A second function was created to generate a simplified investigation report.

Results:

```text
Computer : #############
Analyst  : Shawn
Processes: 342
```

This demonstrated how a script can generate structured investigation output rather than displaying individual command results.

---

### Export Verification

The investigation report was successfully exported to:

```text
Summary.csv
```

This demonstrated how returned data can be preserved and shared outside of PowerShell.

---

## 🧠 Analyst Reflection

This lesson demonstrated how individual PowerShell concepts can be combined into a practical investigation tool.

Instead of manually running multiple commands:

```powershell
Get-Process
Get-Service
Get-ChildItem
```

a reusable script can collect the information automatically and present the findings in a consistent format.

This approach reduces repetitive work, improves consistency, and makes evidence collection easier to automate.

The ability to return structured data and export the results is an important step toward building larger security and investigation tools.
