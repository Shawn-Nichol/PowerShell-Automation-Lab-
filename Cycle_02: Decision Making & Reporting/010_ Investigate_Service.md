# 🛡️ Lesson 010: SOC Investigation Challenge - Suspicious Service Check
[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Decision%20Making%20%26%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-SOC%20Investigation-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Service%20Triage%20%26%20Parsing-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This challenge required building an interactive PowerShell investigation script to determine whether a Windows service exists and identify its current status.

The objective was to apply variables, user input, conditional logic, and service enumeration to perform a basic SOC-style investigation and generate useful information for further analysis.


## 🎯 Challenge Scenario

A security alert indicated that a Windows service may be involved in suspicious activity.

As the investigating analyst, I needed to determine:

- Whether the service exists.
- Whether the service is currently running.
- What information should be gathered next if additional investigation is required.


## 🔎 Questions to Answer

### 1. Does the service exist?

### 2. What is the service's current status?

### 3. What additional information would help determine whether the service is legitimate or suspicious?

Examples:

- Service owner
- Associated executable
- Running process information
- Application purpose
- Startup configuration


## 🧠 Investigation Approach

To answer these questions, I:

1. Prompted the analyst for a service name.
2. Queried the service using `Get-Service`.
3. Verified whether the service existed.
4. Reviewed the current service status.
5. Generated an investigation report containing key service details.


## 💻 My Solution

```powershell
# Get user input (Store as a string)
$serviceName = Read-Host "Enter service"

# Query the service object
$serviceObj = Get-Service -Name $serviceName -ErrorAction SilentlyContinue

# Determine existence and current state
if($serviceObj) {

    Write-Host "$serviceName exists and status is: $($serviceObj.Status)`n"

    # Investigation report
    [PSCustomObject]@{
        "Service Name" = $serviceObj.Name
        "DisplayName" = $serviceObj.DisplayName
        "Status" = $serviceObj.Status
        "Start Type" = $serviceObj.StartType
    } | Format-Table -AutoSize

}
else {

    Write-Host "Service '$serviceName' was not found on this system." -ForegroundColor Red

}
```
<img width="412" height="123" alt="image" src="https://github.com/user-attachments/assets/fd8927ea-3a20-487d-ba2c-0b500bde2980" />


## 🎯 Investigation Results

The script successfully:

- Accepted analyst input.
- Checked whether the service existed.
- Identified the service status.
- Displayed service information in a readable format.
- Generated a basic investigation report.


## 🧠 What I Learned

- Learned how to build an interactive investigation script using `Read-Host`.
- Applied conditional logic to validate evidence.
- Used `Get-Service` to investigate Windows services.
- Practiced using objects to present investigation results.
- Learned that determining whether a service exists is only the first step of an investigation.


## 🔐 Analyst Reflection

A service being present and running does not automatically mean it is legitimate.

Additional evidence that should be collected during a security investigation includes:

- Service executable path
- Service owner
- Digital signature information
- Startup type
- Associated processes
- Network activity
- Business purpose

This challenge reinforced the idea that cybersecurity investigations focus on gathering and validating evidence before making conclusions.


## ✅ Challenge Outcome

Completed the Service Health Investigation Challenge by creating a PowerShell script that:

- Accepts user input.
- Validates service existence.
- Reports service status.
- Produces investigation output suitable for initial SOC triage.
