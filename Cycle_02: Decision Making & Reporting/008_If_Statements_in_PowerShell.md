# 🛡️ If Statements in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Decision%20Making%20%26%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Conditional%20Triage-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-If--Else%20Logic-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced PowerShell if statements and conditional logic. By evaluating conditions and responding accordingly, PowerShell can make decisions based on system information and investigation results.


## 🎯 Learning Objective

Learn how to use if and else statements to create logic-based decisions in PowerShell scripts.


## 🔐 Cybersecurity Application

Security analysts use conditional logic to identify unusual conditions and automate responses. If statements can be used to detect stopped services, high process counts, failed checks, and other indicators that may require investigation.


## ✅ Key Takeaways

- If statements allow PowerShell to make decisions.
- Conditions evaluate to either true or false.
- Comparison operators are used to test values.
- Else statements provide an alternative action.
- Conditional logic is fundamental to automation and security monitoring.


## 💻 PowerShell Commands

```powershell
if (5 -gt 3) {
    "5 is greater than 3"
}
```
<img width="263" height="120" alt="image" src="https://github.com/user-attachments/assets/26461856-2acd-4f88-a7c5-56f87cf0280a" />

```powershell
$Service = Get-Service spooler

if ($Service.Status -eq "Running") {
    "Service is healthy"
} else {
    "Service is not running"
}
```
<img width="367" height="145" alt="image" src="https://github.com/user-attachments/assets/ff6eda3f-89ca-4e5e-9ad6-5007941948c1" />


## 🧠 What I Learned

- Learned how PowerShell evaluates true and false conditions.
- Practiced using comparison operators such as `-eq` and `-gt`.
- Used variables inside if statements to make decisions.
- Learned how else statements provide alternative outcomes.
- Gained an understanding of how conditional logic supports cybersecurity monitoring and automation.
