# 🛡️ Filtering Data with Where-Object

---

## 📌 Executive Summary

This session introduced PowerShell filtering using `Where-Object`. Instead of reviewing every object returned by a command, I learned how to isolate only the data relevant to an investigation.

---

## 🎯 Learning Objective

Learn how to filter PowerShell objects based on property values.

---

## 🔐 Cybersecurity Application

Filtering is essential during investigations because analysts rarely need every result. Using `Where-Object` allows rapid identification of suspicious processes, service states, and system conditions.

---

## ✅ Key Takeaways

- `Where-Object` filters objects based on property values.
- Comparison operators help define filtering conditions.
- Running and stopped services can be isolated quickly.
- Process investigations often begin by filtering large datasets.

---

## 💻 PowerShell Commands

```powershell
Get-Service |
Where-Object Status -eq 'Running'
```

```powershell
Get-Service |
Where-Object Status -eq 'Stopped'
```

```powershell
Get-Process |
Where-Object ProcessName -like '*powershell*'
```

```powershell
Get-Process |
Where-Object Responding -eq $false
```

---

## 🧠 What I Learned

- How to filter data instead of reviewing entire outputs.
- How to use comparison operators.
- How to find specific services and processes.
- How filtering supports cybersecurity investigations.

---

## 🚀 Next Step

Apply command discovery, object inspection, property selection, and filtering together in a cybersecurity investigation challenge.
