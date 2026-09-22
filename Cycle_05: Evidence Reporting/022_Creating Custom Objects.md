# 🛡️ Creating Custom Objects in PowerShell

[![PowerShell](https://img.shields.io/badge/PowerShell-7%2B-5391FE?logo=powershell&logoColor=white)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Category](https://img.shields.io/badge/Category-Evidence%20Reporting-blue)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Security](https://img.shields.io/badge/Security-Investigation%20Reporting-red)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)
[![Concept](https://img.shields.io/badge/Concept-PSCustomObject-orange)](https://github.com/Shawn-Nichol/PowerShell-Automation-Lab-)

## 📌 Executive Summary

This lesson introduced `PSCustomObject`, a PowerShell feature used to create structured data and custom investigation reports. By defining custom properties, analysts can organize investigation findings into reusable objects that can be displayed, exported, filtered, and included in reporting workflows.


## 🎯 Learning Objective

Learn how to create custom PowerShell objects and use them to structure investigation data for reporting and evidence collection.


## 🔐 Cybersecurity Application

Security analysts frequently convert collected evidence into structured reports. Rather than relying on notes or console output, `PSCustomObject` allows findings to be organized into fields that can be exported, shared, and reused throughout an investigation.

Common uses include:

- Investigation summaries
- Process inventories
- Service audits
- File reviews
- Incident response reports
- Security dashboards


## ✅ Key Takeaways

- `PSCustomObject` creates custom PowerShell objects.
- Properties can be defined using key/value pairs.
- Structured data is easier to export and report on.
- Custom objects can be filtered, sorted, and reused.
- Investigation findings can be standardized using custom objects.
- PSCustomObjects work well with CSV exports.


## 💻 PowerShell Commands

### Create an Analyst Record

```powershell
[PSCustomObject]@{
    Analyst = "Shawn N"
    Computer = "AwesomO5000"
}
```

<img width="347" height="161" alt="image" src="https://github.com/user-attachments/assets/96f1689f-73bf-45a1-a7c0-0a878b288c39" />


---

### Create a Filesystem Summary

```powershell
[PSCustomObject]@{
    TotalFiles = $files.Count
    Executables = $exe.Count
    HiddenFiles = $hidden.Count
}
```

<img width="367" height="166" alt="image" src="https://github.com/user-attachments/assets/b7e1cc74-512e-4e4f-9232-c0cf7fc1d486" />


### Create an Investigation Report

```powershell
[PSCustomObject]@{
    LargestFile = "Windows.iso"
    FileCount = $files.Count
    Assessment = "No suspicious artifacts identified"
}
```

<img width="513" height="172" alt="image" src="https://github.com/user-attachments/assets/2fee2835-0123-4df0-8517-3d9b329fe529" />


---

## 🧠 What I Learned

- Learned how to create custom PowerShell objects.
- Practiced defining properties using key/value pairs.
- Created structured investigation summaries.
- Used PowerShell variables inside custom objects.
- Learned how custom objects improve evidence reporting.
- Gained an understanding of how structured reporting supports cybersecurity investigations.


## 🔍 Investigation Notes

### Analyst Record

A custom object was created containing:

```text
Analyst Name
Computer Name
```

Example:

```text
Analyst : Shawn N
Computer : AwesomO5000
```

This demonstrates how PowerShell objects can be used to document investigation ownership and system information.

---

### Filesystem Summary

A custom report object was created to summarize:

```text
Total Files
Executables
Hidden Files
```

Results:

```text
Total Files: 178
Executables: 27
Hidden Files: 50
```

This provided a quick inventory summary without requiring multiple commands.

---

### Investigation Summary Report

A final custom object was used to summarize key findings:

```text
Largest File: Windows.iso
Assessment: No suspicious artifacts identified
```

This demonstrated how investigation conclusions can be standardized into report-friendly formats.

---

## 🧠 Analyst Reflection

A major challenge in cybersecurity is turning collected evidence into meaningful reports.

Without custom objects:

```text
Evidence exists in multiple commands and outputs.
```

With custom objects:

```text
Evidence can be organized into structured records.
```

This makes reporting easier and allows findings to be exported to CSV files, included in investigation reports, and shared with other analysts.
