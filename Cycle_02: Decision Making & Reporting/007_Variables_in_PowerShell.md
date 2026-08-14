# 🛡️ Variables in PowerShell


## 📌 Executive Summary

This lesson introduced PowerShell variables and demonstrated how they can be used to store and reuse information efficiently. Variables can hold text, numbers, and entire PowerShell objects, making them a fundamental tool for automation and cybersecurity investigations.


## 🎯 Learning Objective

Learn how to create variables and use them to store different types of data in PowerShell, including text values, numbers, and PowerShell objects.


## 🔐 Cybersecurity Application

Security analysts frequently use variables to store evidence collected during investigations. Process information, service details, and system data can be gathered once and reused throughout an investigation script, reducing repetitive commands and improving efficiency.

## ✅ Key Takeaways

- Variables begin with the `$` symbol.
- Variables can store text, numbers, and PowerShell objects.
- PowerShell objects stored in variables retain all their properties and methods.
- Variables reduce repetitive commands and improve script readability.
- Variables are a foundational component of automation and security investigations.



## 💻 PowerShell Commands

```powershell
$Computer = "Workstation01"
```
<img width="331" height="53" alt="image" src="https://github.com/user-attachments/assets/a4e0d947-7276-4cb0-9d57-3ab3025baab2" />


```powershell
$Service = Get-Service spooler
```
<img width="352" height="151" alt="image" src="https://github.com/user-attachments/assets/0bae6eef-2bb9-4eac-8ba4-ddf932affddd" />


```powershell
$Service.Status
```
<img width="230" height="43" alt="image" src="https://github.com/user-attachments/assets/b4936008-a27f-4a67-b856-2ab9c5fd5849" />


```powershell
$Processes = Get-Process
```
<img width="857" height="287" alt="image" src="https://github.com/user-attachments/assets/085c5503-03fd-4658-a473-320fc4536991" />


```powershell
$Processes.Count
```
<img width="228" height="34" alt="image" src="https://github.com/user-attachments/assets/85bc8380-453e-4313-80cd-1101e80f2eda" />


```powershell
$Chrome = Get-Process chrome
```

```powershell
$Chrome.ProcessName
```
<img width="590" height="355" alt="image" src="https://github.com/user-attachments/assets/a2f7d1c4-5144-4566-acd9-d58ef8175e20" />


```powershell
$Chrome.CPU
```
<img width="226" height="407" alt="image" src="https://github.com/user-attachments/assets/fd82f09a-b0e4-4b96-bd10-8e613b0e1912" />

```powershell
$Chrome.Id
```
<img width="202" height="290" alt="image" src="https://github.com/user-attachments/assets/44443309-7c19-4a7d-b8a1-d97e5e440750" />


## 🧠 What I Learned
- Learned how to create and use PowerShell variables.
- Stored text, numbers, and PowerShell objects in variables.
- Accessed object properties from stored variables.
- Reduced repetitive commands by reusing stored data.
- Gained a better understanding of how variables are used during cybersecurity investigations.
