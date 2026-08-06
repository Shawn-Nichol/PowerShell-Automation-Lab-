# 🛡️ Discovering PowerShell Commands
![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-blue?logo=powershell)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-brightgreen)
![Category](https://img.shields.io/badge/Category-Command%20Discovery-blue)
![Security](https://img.shields.io/badge/Security-Cybersecurity-red)
![Concept](https://img.shields.io/badge/Concept-Help%20System-orange)


images/get-command-discovery-hero.png

## 📌 Executive Summary

This lab introduced PowerShell command discovery and the built-in help system. I learned how to locate relevant commands using wildcards, read documentation using Get-Help, and view running processes. These skills form the foundation for future cybersecurity investigations.

---

## 🎯 Learning Objective

Learn how to discover PowerShell commands and understand their usage through PowerShell's built-in help system.

---

## 🚀 Key Highlights

- Used `Get-Command` to discover available commands.
- Used wildcards to find related cmdlets.
- Used `Get-Help` to access examples and documentation.
- Viewed running processes with `Get-Process`.
- Connected process enumeration to cybersecurity investigations.

---

## 🔐 Cybersecurity Application

Cybersecurity analysts regularly encounter unfamiliar systems. The ability to discover commands and read built-in documentation allows analysts to investigate processes, services, logs, and system settings efficiently without relying on memorization.

---

## 💻 PowerShell Commands

```powershell
Get-Command
```
<img width="872" height="581" alt="image" src="https://github.com/user-attachments/assets/6989b295-dea5-4ebf-be2c-fe8f5226e22a" />

```powershell
Get-Command *process*
```
<img width="930" height="386" alt="image" src="https://github.com/user-attachments/assets/1b3c5ade-0358-4047-bebc-b64bf7811d91" />

```powershell
Get-Command *service*
```

```powershell
Get-Help Get-Service -Examples
```
<img width="941" height="499" alt="image" src="https://github.com/user-attachments/assets/dba2cb8a-808d-42a5-a288-2cb82a2f9f9e" />


```powershell
Get-Process |
Select-Object -First 10
```
<img width="846" height="300" alt="image" src="https://github.com/user-attachments/assets/b13e4574-e982-474e-8f54-7fdb8779b9ae" />

---

## ✅ Key Takeaways

- PowerShell commands can be discovered instead of memorized.
- Wildcards make searching for commands easy.
- Get-Help provides built-in documentation and examples.
- Process visibility is a core cybersecurity skill.
