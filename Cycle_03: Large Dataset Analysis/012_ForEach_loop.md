# 🛡️ ForEach in PowerShell
[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Large%20Dataset%20Analysis-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-IOC%20Investigation-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-ForEach%20Loops-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
## 📌 Executive Summary

This lesson introduced the `ForEach` loop, which allows PowerShell to perform the same action against every item stored in a collection. By combining arrays and loops, repetitive investigation tasks can be automated and scaled across larger datasets.

## 🎯 Learning Objective

Learn how to use `ForEach` to process multiple items stored within an array.

## 🔐 Cybersecurity Application

Security analysts often work with collections of indicators such as suspicious processes, services, IP addresses, file hashes, and user accounts. The `ForEach` loop makes it possible to perform the same investigation across every item in a dataset without manually repeating commands.

## ✅ Key Takeaways

- `ForEach` processes each item in a collection.
- Loops reduce repetitive coding.
- Arrays and `ForEach` work together.
- Each iteration uses a temporary variable.
- Automation improves investigation efficiency.
- SOC analysts use loops when reviewing large numbers of indicators.

## 💻 PowerShell Commands

```powershell
$processes = "powershell","cmd","notepad"

foreach ($process in $processes)
{
    Write-Host $process
}
```

<img width="492" height="175" alt="image" src="https://github.com/user-attachments/assets/ad913276-034e-440a-be0b-30667f6a330d" />


```powershell
$iocs = "powershell.exe","wscript.exe","mshta.exe"

foreach ($ioc in $iocs)
{
    Write-Host "Reviewing IOC: $ioc"
}
```

<img width="535" height="148" alt="image" src="https://github.com/user-attachments/assets/5da31eed-dac9-4fb1-870a-ef6c146eb94d" />



```powershell
$services = "BITS","Spooler","WinRM"

foreach ($service in $services)
{
    Write-Host "Checking Service: $service"
}
```
<img width="436" height="146" alt="image" src="https://github.com/user-attachments/assets/651e663c-8190-4838-91fd-d93411427bfe" />




## 🧠 What I Learned

- Learned how `ForEach` loops process collections of data.
- Practiced iterating through arrays one item at a time.
- Used temporary variables during each loop iteration.
- Reduced repetitive commands through automation.
- Gained an understanding of how loops support threat hunting and large-scale investigations.
