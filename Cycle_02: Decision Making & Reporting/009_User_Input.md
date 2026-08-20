# 🛡️ User Input with Read-Host
[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Decision%20Making%20%26%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Interactive%20Triage-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-User%20Input-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced the PowerShell `Read-Host` cmdlet and interactive scripting. By allowing users to provide input at runtime, scripts become more flexible, reusable, and useful for investigations without requiring code modifications.


## 🎯 Learning Objective

Learn how to collect user input using `Read-Host`, store the results in variables, and use the supplied information throughout a PowerShell script.


## 🔐 Cybersecurity Application

Security analysts frequently investigate different users, processes, services, computers, and files. Rather than hard-coding values into scripts, `Read-Host` allows analysts to supply investigation targets at runtime, making scripts more adaptable and efficient during troubleshooting, security monitoring, and incident response activities.


## ✅ Key Takeaways

- Read-Host allows PowerShell scripts to request input from a user.
- User input can be stored in variables for later use.
- Interactive scripts are more reusable than hard-coded scripts.
- Read-Host works well with variables and conditional logic.
- Analysts can investigate different assets without modifying script code.


## 💻 PowerShell Commands

### Basic User Input

```powershell
$name = Read-Host "Enter your name"

Write-Host "Hello $name"
```
<img width="414" height="124" alt="image" src="https://github.com/user-attachments/assets/f0bfdbdd-ecb2-47f3-abbe-b6a195cb9929" />

### Process Investigation

```powershell
$process = Read-Host "Enter process name"

Get-Process -Name $process
```

<img width="605" height="149" alt="image" src="https://github.com/user-attachments/assets/1af2fe38-391e-47a8-8b60-57d85d62288f" />


### Service Investigation

```powershell
$service = Read-Host "Enter service name"

Get-Service -Name $service
```
<img width="468" height="139" alt="image" src="https://github.com/user-attachments/assets/6b0b1069-d668-47b7-ae2f-9774dec593c5" />


### Service Existence Check

```powershell
$service = Read-Host "Enter service name"

$result = Get-Service -Name $service -ErrorAction SilentlyContinue

if ($result)
{
    Write-Host "Service Found"
}
else
{
    Write-Host "Service Not Found"
}
```
<img width="618" height="255" alt="image" src="https://github.com/user-attachments/assets/190aeb18-702c-4d25-9361-95b0d16d8825" />


### Service Health Investigation

```powershell
$service = Read-Host "Enter service name"

$result = Get-Service -Name $service

Write-Host "==== Investigation Report ===="
Write-Host "Service:" $result.Name
Write-Host "Status:" $result.Status
```
<img width="414" height="197" alt="image" src="https://github.com/user-attachments/assets/aa506762-e311-4b02-bd3a-befc0da51e00" />


### Multiple Inputs

```powershell
$user = Read-Host "Enter username"
$computer = Read-Host "Enter computer name"

Write-Host "Investigating $user on $computer"
```
<img width="440" height="122" alt="image" src="https://github.com/user-attachments/assets/e6e39b5b-6fe0-4b75-941f-5e7f75cd67cb" />


## 🧠 What I Learned

- Learned how to collect user input using Read-Host.
- Practiced storing user-provided information in variables.
- Used interactive input to investigate processes and services.
- Combined Read-Host with variables and conditional logic.
- Gained an understanding of how interactive scripts improve cybersecurity investigations and troubleshooting workflows.



