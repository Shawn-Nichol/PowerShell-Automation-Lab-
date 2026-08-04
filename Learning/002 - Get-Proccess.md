# Get-Process

## 1. Executive Summary

`Get-Process` is a PowerShell cmdlet used to enumerate and inspect running processes on a Windows system. This exercise introduced process investigation techniques and demonstrated how PowerShell can be used to gather information that supports troubleshooting, performance analysis, and cybersecurity investigations.

The most valuable lesson was not learning how to list processes, but learning how to investigate unfamiliar processes, validate assumptions, and recognize when permissions affect the visibility of information.

### Highlights

- Identified 320 running processes on the system.
- Investigated an unfamiliar process, `AggregatorHost.exe`.
- Learned that process information may be hidden without administrative privileges.
- Discovered that process names do not always clearly identify the application responsible for launching them.
- Reinforced the importance of distinguishing evidence from assumptions during an investigation.

---

## 2. Learning Objective

The goal of this exercise was to learn how PowerShell exposes process information and how that information can be used to investigate running applications and system activity.

Specific objectives included:

- Enumerating running processes
- Exploring process object properties
- Identifying resource-intensive processes
- Investigating unfamiliar processes
- Understanding how permissions affect process visibility

---

## 3. Cybersecurity Applications

`Get-Process` is a foundational command for cybersecurity investigations because it provides visibility into what is currently executing on a system.

### Process Enumeration

Analysts can use process enumeration to identify:

- Running applications
- Background services
- Unexpected or unauthorized software
- Resource-intensive processes

### Threat Hunting

Process information can assist with identifying:

- Suspicious process names
- Unusual execution locations
- Unexpected parent-child relationships
- Potential malicious activity

### Incident Response

During an investigation, process information can help determine:

- What was running at the time of collection
- Which processes are consuming abnormal resources
- Whether suspicious activity may be occurring

### Performance Investigation

Processes with excessive memory or CPU utilization can be investigated to determine:

- Application issues
- Resource exhaustion
- Potential malware activity

---

## 4. Security Scenario

A user reports that their system has become slow and unresponsive.

An analyst's first task is to determine which processes are consuming system resources and whether any unexpected applications are running.

Using:

```powershell
Get-Process
```

the analyst can collect information about:

- Running processes
- CPU consumption
- Memory usage
- Process identifiers (PIDs)

Additional investigation can then focus on any process exhibiting unusual behavior.

---

## 5. Key Takeaways

- PowerShell returns process objects rather than plain-text output.
- A process name does not necessarily identify the application a user launched.
- Many legitimate Windows components have names that provide little indication of their purpose.
- Unknown processes should be investigated before being considered suspicious.
- Missing information does not necessarily mean the data does not exist.
- Process information may require elevated privileges to access.
- Process IDs are temporary and should not be treated as permanent identifiers.
- Modern applications often create numerous child processes.

### Valuable Process Properties

The following properties appeared particularly useful from a security perspective:

| Property | Purpose


Valuable Process Properties
The following properties appeared particularly useful from a security perspective:

Property	Purpose
Name	Identify the process
Id	Unique process identifier
CPU	Measure processor utilization
WorkingSet	Current memory consumption
StartTime	Determine when a process started
Path	Locate the executable
Company	Identify the software publisher


## 6. Interesting Discoveries
Permission Affects Visibility
While investigating AggregatorHost.exe, the executable path initially appeared blank using:

Get-Process AggregatorHost |
Select-Object Name, Id, Path
After reopening PowerShell with administrative privileges, the executable path became visible:

C:\Windows\System32\AggregatorHost.exe
This revealed an important investigative lesson:

Missing information does not always mean the information is unavailable. Sometimes additional privileges are required to access it.

Unknown Does Not Mean Malicious
Many process names were unfamiliar during the investigation, including:

AggregatorHost
RuntimeBroker
ApplicationFrameHost
SearchIndexer
LsaIso
DllHost
The exercise reinforced that unfamiliarity alone is not evidence of malicious activity.

Instead, analysts should investigate:

Process location
Publisher
Parent process
Resource consumption
Execution behavior
before drawing conclusions.

Process IDs Change
During the investigation, a restart occurred before follow-up analysis could be completed.

This demonstrated that:

Process IDs (PIDs) are temporary.
PIDs frequently change after a reboot.
Investigations should not rely on process IDs as permanent identifiers.
Modern Applications Spawn Many Processes
One of the most noticeable observations was the number of processes associated with browsers and web-based applications.

Examples included:

Google Chrome
Microsoft Edge WebView (msedgewebview2)
Microsoft Teams
Microsoft 365 Copilot
This demonstrated that modern applications commonly use multi-process architectures to improve:

Stability
Isolation
Security
Performance

## 7. Technical Reference
Syntax
Get-Process
Count Running Processes
(Get-Process).Count
Result:

320
This introduced the use of parentheses to evaluate a command before accessing a property.

View Process Properties
Get-Process | Get-Member
Used to discover available properties and methods.

Sort by Memory Consumption
Get-Process |
Sort-Object WorkingSet -Descending
Useful for identifying resource-intensive processes.

Investigate a Specific Process
Get-Process AggregatorHost |
Select-Object Name, Id, Path
Identify Parent Process Information
Get-CimInstance Win32_Process |
Where-Object {$_.Name -eq "AggregatorHost.exe"} |
Select-Object ProcessId, ParentProcessId, ExecutablePath
Output:

ProcessId       : 10448
ParentProcessId : 5048
ExecutablePath  : C:\Windows\System32\AggregatorHost.exe
8. Hands-on Examples
Example 1: List Running Processes
Get-Process
Purpose:

Enumerate active processes
Establish a baseline of system activity
Example 2: Count Processes
(Get-Process).Count
Purpose:

Determine the total number of running processes
Result:

320
Example 3: Explore Process Objects
Get-Process | Get-Member
Purpose:

Discover available properties
Learn which information can be collected
Example 4: Investigate a Specific Process
Get-Process AggregatorHost |
Select-Object Name, Id, Path
Purpose:

Identify process location
Gather supporting evidence
Result:

C:\Windows\System32\AggregatorHost.exe
Example 5: Identify High-Memory Processes
Get-Process |
Sort-Object WorkingSet -Descending |
Select-Object -First 10
Purpose:

Identify processes consuming the most memory
Prioritize further investigation
## 9. Mistakes
Mistake #1: Assuming Unknown Processes Are Malicious
Unknown processes require investigation.

Unknown does not automatically mean suspicious.

Mistake #2: Treating Process Names as Application Names
A process name does not necessarily reveal:

Which application owns it
Why it is running
Whether it was launched directly by the user
Additional investigation is often required.

Mistake #3: Ignoring Permissions
Some process information may not be available without administrative privileges.

Investigators should verify whether missing information is permission-related before assuming the data is unavailable.

Mistake #4: Treating PIDs as Permanent
Process IDs change:

Between reboots
Between launches
Between process instances
PIDs should only be used as temporary identifiers.

## 10. Related Commands
Get-Member
Explore object properties and methods.

Get-Member
Get-CimInstance
Retrieve additional process information.

Get-CimInstance Win32_Process
Where-Object
Filter process collections.

Where-Object
Sort-Object
Sort processes by memory, CPU, or other properties.

Sort-Object
Select-Object
Display only relevant information.

Select-Object
Stop-Process
Terminate a running process.

Stop-Process
