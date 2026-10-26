# 🛡️ Try/Catch Error Handling

[![PowerShell 7+](https://img.shields.io/badge/PowerShell-7%2B-239120?style=for-the-badge&logo=powershell&logoColor=white)](https://github.com/PowerShell/PowerShell)
[![Difficulty: Beginner](https://img.shields.io/badge/Difficulty-Beginner-brightgreen?style=for-the-badge)](https://github.com/)
[![Category: Reliable Investigations](https://img.shields.io/badge/Category-Reliable%20Investigations-orange?style=for-the-badge)](https://github.com/)
[![Security: Error Handling](https://img.shields.io/badge/Security-Error%20Handling-blueviolet?style=for-the-badge)](https://github.com/)
[![Concept: Try/Catch](https://img.shields.io/badge/Concept-Try%2FCatch-informational?style=for-the-badge)](https://github.com/)

---

## 📌 Executive Summary

This lesson introduced PowerShell Try/Catch error handling. Rather than simply hiding errors, Try/Catch allows scripts to detect failures and respond appropriately. This improves reliability and helps investigation tools continue operating even when processes, services, or files cannot be found.

---

## 🎯 Learning Objective

Learn how to use Try/Catch blocks to detect and handle errors during PowerShell investigations.

---

## 🔐 Cybersecurity Application

Security investigations regularly encounter missing processes, unavailable services, deleted files, and access restrictions.

Try/Catch allows scripts to:

- Detect failures
- Continue collecting evidence
- Present meaningful feedback
- Reduce troubleshooting time
- Improve automation reliability

Error handling is an important part of building resilient investigation tools.

---

## ✅ Key Takeaways

- The `try` block contains code PowerShell attempts to execute.
- The `catch` block executes when a terminating error occurs.
- `-ErrorAction Stop` forces errors into the catch block.
- Try/Catch allows scripts to handle failures gracefully.
- Investigation tools should anticipate missing data.
- Error handling improves script reliability and usability.

---

## 💻 PowerShell Commands

### Process Investigation

```powershell
try {

    Get-Process explorer -ErrorAction Stop

} catch {

    "Process not found"

}
```

<img width="542" height="153" alt="image" src="https://github.com/user-attachments/assets/605be827-bbbc-4283-aba1-178d7bbb92f3" />


---

### Missing Process Example

```powershell
try {

    Get-Process TotallyFakeProcess -ErrorAction Stop

} catch {

    "Process not found"

}
```

Output:

```text
Process not found
```

<img width="499" height="102" alt="image" src="https://github.com/user-attachments/assets/dd15d5f8-1a31-43fb-81aa-ac2ad6103299" />


---

### Missing Service Example

```powershell
try {

    Get-Service FakeService -ErrorAction Stop

} catch {

    "Service not found"

}
```

Output:

```text
Service not found
```

<img width="446" height="96" alt="image" src="https://github.com/user-attachments/assets/0d3f1e2e-eeb0-4472-88f1-cd56e5e74ab0" />


---

### Safer Investigation Function

```powershell
function Get-ProcessInfo {

    Param(
        $Name
    )

    try {

        Get-Process $Name -ErrorAction Stop

    } catch {

        "Process not found"

    }

}
```

<img width="581" height="314" alt="image" src="https://github.com/user-attachments/assets/e64bed2f-0053-4e80-af7a-951f1271b4c1" />


---

## 🧠 What I Learned

- Learned how Try/Catch handles PowerShell errors.
- Practiced detecting missing processes and services.
- Used `-ErrorAction Stop` to trigger catch blocks.
- Improved investigation script reliability.
- Learned how to provide meaningful feedback when errors occur.
- Gained a better understanding of resilient automation practices.

---

## 🔍 Investigation Notes

### Missing Process Investigation

Attempting to query a non-existent process generated an error.

Using Try/Catch allowed the error to be replaced with a more useful response:

```text
Process not found
```

---

### Missing Service Investigation

Attempting to query a non-existent service produced a similar result.

Instead of displaying raw PowerShell errors, the script returned:

```text
Service not found
```

This created cleaner investigation output.

---

### Investigation Function

A safer version of `Get-ProcessInfo` was created using Try/Catch.

Benefits included:

- Cleaner output
- Better user experience
- Reduced script interruptions
- Improved automation reliability

---

## 🧠 Analyst Reflection

Investigation tools should expect things to go wrong.

Processes may terminate.

Services may not exist.

Files may be deleted.

Instead of allowing a script to fail unexpectedly, Try/Catch provides a controlled way to respond to issues while continuing the investigation.

This makes scripts more reliable and produces cleaner, more professional output during security investigations.
