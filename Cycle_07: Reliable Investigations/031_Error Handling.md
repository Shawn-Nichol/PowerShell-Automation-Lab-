# 🛡️ Error Handling Basics


![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-blue?style=for-the-badge&logo=powershell&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-Reliable%20Investigations-orange?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Error%20Handling-critical?style=for-the-badge)
![Concept](https://img.shields.io/badge/Concept-Investigation%20Reliability-informational?style=for-the-badge)
---

## 📌 Executive Summary

This lesson introduced basic PowerShell error handling techniques. During investigations, processes, services, files, and other resources may not exist. Error handling helps ensure scripts continue operating correctly without producing unnecessary error messages.

---

## 🎯 Learning Objective

Learn how to identify PowerShell errors and use `-ErrorAction SilentlyContinue` to create more reliable investigation scripts.

---

## 🔐 Cybersecurity Application

Security investigations often involve searching for artifacts that may not exist.

Examples include:

- Missing processes
- Missing services
- Deleted files
- Uninstalled applications

Without error handling, investigation scripts become difficult to read and maintain.

Basic error handling improves script reliability and helps maintain clean investigation output.

---

## ✅ Key Takeaways

- PowerShell commands can generate errors when objects are not found.
- Errors and warnings are different types of messages.
- `-ErrorAction SilentlyContinue` suppresses error messages.
- Investigation scripts should be designed to handle missing data gracefully.
- Error handling improves automation reliability.
- Functions can incorporate error handling techniques.

---

## 💻 PowerShell Commands

### Generate a Process Error

```powershell
Get-Process TotallyFakeProcess
```

Output:

```text
Cannot find a process with the name "TotallyFakeProcess".
```

<img width="1100" height="47" alt="image" src="https://github.com/user-attachments/assets/acf70cff-c3f3-4b7a-8c5f-5d66e51df306" />


---

### Suppress Process Error

```powershell
Get-Process TotallyFakeProcess -ErrorAction SilentlyContinue
```

Output:

```text
(no output)
```

<img width="664" height="62" alt="image" src="https://github.com/user-attachments/assets/7eaaca2b-a926-44ab-b74c-e20c79efc1e3" />


---

### Generate a Service Error

```powershell
Get-Service FakeService
```

Output:

```text
Cannot find any service with service name 'FakeService'.
```

<img width="655" height="50" alt="image" src="https://github.com/user-attachments/assets/41f6d5e8-310a-48e5-b041-7236c4dd9a09" />


---

### Suppress Service Error

```powershell
Get-Service FakeService -ErrorAction SilentlyContinue
```

Output:

```text
(no output)
```

<img width="640" height="42" alt="image" src="https://github.com/user-attachments/assets/a469ae5c-8142-4597-afae-70d08d3c55c6" />


---

### Safer Investigation Function

```powershell
function Get-ProcessInfo {

    Param(
        $Name
    )

    Get-Process $Name -ErrorAction SilentlyContinue
}
```

Example:

```powershell
Get-ProcessInfo -Name NotRealProcess
```

Output:

```text
(no output)
```

<img width="561" height="217" alt="image" src="https://github.com/user-attachments/assets/245e31ab-4304-44d4-a5f7-5d5630cc1e80" />


---

## 🧠 What I Learned

- Learned how PowerShell responds when requested objects do not exist.
- Practiced generating and reviewing error messages.
- Suppressed expected errors using `-ErrorAction SilentlyContinue`.
- Improved the reliability of investigation functions.
- Learned how error handling supports automation.

---

## 🔍 Investigation Notes

### Process Investigation

Searching for a non-existent process generated an error:

```text
Cannot find a process with the name "TotallyFakeProcess".
```

When:

```powershell
-ErrorAction SilentlyContinue
```

was applied, the error was hidden and no output was returned.

---

### Service Investigation

Searching for a non-existent service generated a similar error.

Adding:

```powershell
-ErrorAction SilentlyContinue
```

allowed the command to continue without displaying the error message.

---

### Function Reliability

A safer process investigation function was created:

```powershell
Get-ProcessInfo
```

The function was able to handle non-existent process names without generating unnecessary errors.

This makes the function more suitable for automation.

---

## 🧠 Analyst Reflection

Investigation scripts should not fail simply because an expected process or service is missing.

Using:

```powershell
-ErrorAction SilentlyContinue
```

helps reduce unnecessary output and creates cleaner reports.

While errors should not always be ignored, understanding how to control them is an important step toward building reliable investigation tools.
