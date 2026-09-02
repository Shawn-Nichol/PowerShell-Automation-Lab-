# 🛡️ for Loops in PowerShell

![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)
![Category](https://img.shields.io/badge/Category-Large%20Dataset%20Analysis-blue)
![Security](https://img.shields.io/badge/Security-Alert%20Analysis-red)
![Concept](https://img.shields.io/badge/Concept-for%20Loops-orange)
## 📌 Executive Summary

This lesson introduced PowerShell `for` loops, which allow an action to be repeated a specific number of times. Unlike `ForEach`, which processes each item in a collection, `for` loops are useful when the number of repetitions is known in advance.

## 🎯 Learning Objective

Learn how to use `for` loops to perform repetitive actions and understand when to use them instead of `ForEach` loops.


## 🔐 Cybersecurity Application

Security analysts frequently encounter situations where the number of events, alerts, or investigation steps is known ahead of time. `for` loops can be used to automate repetitive tasks such as reviewing alert numbers, processing event sequences, or generating investigation checkpoints.


## ✅ Key Takeaways

- `for` loops repeat actions a specific number of times.
- A `for` loop contains a starting value, condition, and increment.
- The loop continues until the condition evaluates to false.
- `for` loops are useful when the number of repetitions is known.
- `ForEach` loops are better suited for collections of data.
- Loops help automate repetitive investigation tasks.

---

## 💻 PowerShell Commands

```powershell
for ($i = 1; $i -le 5; $i++)
{
    Write-Host $i
}
```
<img width="391" height="172" alt="image" src="https://github.com/user-attachments/assets/0fddd7f8-0570-45e4-9954-0fe0a41e6715" />

---

```powershell
for ($alert = 1; $alert -le 5; $alert++)
{
    Write-Host "Alert $alert"
}
```

<img width="494" height="175" alt="image" src="https://github.com/user-attachments/assets/77238e7c-4de1-4a35-92df-18b26db9b208" />

---
```powershell
for ($step = 1; $step -le 3; $step++)
{
    Write-Host "Step $step"
}
```
<img width="460" height="154" alt="image" src="https://github.com/user-attachments/assets/bbc61aa0-5970-46a9-9b27-ea46b99004ee" />

---
```powershell
for ($event = 1; $event -le 5; $event++)
{
    Write-Host "Reviewing Event $event"
}
```

<img width="452" height="189" alt="image" src="https://github.com/user-attachments/assets/d61eb8c5-0d05-40dd-bb7d-97084a0cf548" />

---
```powershell
$processes = "powershell","cmd","notepad"

for ($i = 0; $i -lt $processes.Count; $i++)
{
    Write-Host $processes[$i]
}
```

<img width="404" height="195" alt="image" src="https://github.com/user-attachments/assets/944c8370-77e4-4436-903e-86f220756594" />



## 🧠 What I Learned

- Learned how `for` loops repeat actions a specific number of times.
- Practiced using a starting value, condition, and increment.
- Identified situations where a `for` loop is more appropriate than a `ForEach` loop.
- Used loops to simulate reviewing alerts and events.
- Learned how arrays can be accessed using indexes within a `for` loop.
- Gained an understanding of how loops support automation and security investigations.
