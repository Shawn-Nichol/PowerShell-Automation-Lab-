# 🛡️ Arrays in PowerShell
[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Large%20Dataset%20Analysis-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-IOC%20Management-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-Arrays-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced PowerShell arrays, which allow multiple values to be stored within a single variable. Arrays make it easier to manage collections of information and are commonly used when working with processes, services, files, user accounts, and Indicators of Compromise (IOCs).


## 🎯 Learning Objective

Learn how to create arrays, access individual elements, count items, and add additional values to an existing collection.


## 🔐 Cybersecurity Application

Security analysts rarely investigate a single item at a time. Arrays provide a way to organize groups of suspicious processes, services, file names, user accounts, or Indicators of Compromise (IOCs) so they can be analyzed more efficiently and prepared for automation.


## ✅ Key Takeaways

- Arrays store multiple values in a single variable.
- Arrays use zero-based indexing.
- Individual values can be retrieved using their index number.
- The `.Count` property returns the number of items in an array.
- Arrays can grow by adding new values.
- Arrays are foundational for threat hunting and large dataset analysis.


## 💻 PowerShell Commands

```powershell
$processes = "powershell","cmd","notepad"
```

<img width="598" height="105" alt="image" src="https://github.com/user-attachments/assets/0e91b24f-a3dd-48d5-88ec-9a58601ef760" />


```powershell
$processes.Count
```

<img width="281" height="47" alt="image" src="https://github.com/user-attachments/assets/b883979c-1088-4940-b8ad-37a8e296da34" />


```powershell
$processes[1]
```

<img width="349" height="44" alt="image" src="https://github.com/user-attachments/assets/a3579bac-df38-4e05-a817-acc5aafc0ba2" />


```powershell
$processes += "chrome"

$processes
```

<img width="385" height="135" alt="image" src="https://github.com/user-attachments/assets/a2ce777e-c6c3-4905-aa59-e6568640e65f" />



## 🧠 What I Learned

- Learned how to store multiple values in a single variable using arrays.
- Practiced accessing individual items using index numbers.
- Learned that PowerShell arrays begin at index 0.
- Used the `.Count` property to determine the number of elements in an array.
- Added new values to an existing array.
- Gained an understanding of how arrays help organize evidence during cybersecurity investigations.

