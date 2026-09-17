# 🛡️ Lesson 020: Suspicious Files Review Challenge

---

## 📌 Executive Summary

This challenge focused on performing a filesystem investigation of the Downloads directory. The objective was to identify potentially suspicious files by reviewing file counts, large files, executable files, hidden files, and overall directory contents.

The investigation applied the file discovery, attribute analysis, and file filtering techniques learned throughout the Filesystem Investigation cycle.

---

## 🎯 Challenge Scenario

A user reported unusual system behavior after downloading multiple files.

As the investigating analyst, I was tasked with:

- Reviewing the Downloads directory.
- Identifying large files.
- Reviewing executable files.
- Examining hidden files.
- Providing an overall assessment of potential risks.

---

## 🔎 Questions to Answer

### 1. How many files were identified?

### 2. Which files were the largest?

### 3. Which executable files required review?

### 4. Were any hidden files identified?

### 5. What conclusions can be drawn from the investigation?

---

## 🧠 Investigation Approach

To answer these questions, I:

1. Collected all files from the Downloads directory.
2. Counted the total number of files.
3. Sorted files by size to identify the largest artifacts.
4. Filtered executable files for review.
5. Reviewed hidden files and their attributes.
6. Documented findings and observations.

---

## 💻 My Solution

### Collect Files

```powershell
$file = Get-ChildItem "$env:USERPROFILE\Downloads" -Force
```
<img width="571" height="53" alt="image" src="https://github.com/user-attachments/assets/6b493ea9-cb9e-48e7-806a-498978500510" />

---

### Count Files

```powershell
$file.Count
```

<img width="288" height="35" alt="image" src="https://github.com/user-attachments/assets/9a15c8af-067d-49c6-9f27-395b7e85e31c" />


### Identify Largest Files

```powershell
$file |
    Sort-Object Length -Descending |
    Select-Object -First 5 Name, Length
```

<img width="686" height="182" alt="image" src="https://github.com/user-attachments/assets/365e6267-b9b7-4010-ab30-0294ae511d6b" />

---

### Count Executables

```powershell
($file | Where-Object Extension -eq ".exe").Count
```

<img width="485" height="44" alt="image" src="https://github.com/user-attachments/assets/2690b7da-1abc-474e-81dc-5a4e65b2a3ce" />

---

### Review Executables

```powershell
$file |
    Where-Object Extension -eq ".exe"
```

<img width="716" height="259" alt="image" src="https://github.com/user-attachments/assets/70956888-fca6-4924-8a88-892567608d9a" />

---

### Find Newest Executable

```powershell
$file |
    Where-Object Extension -eq ".exe" |
    Sort-Object LastWriteTime -Descending |
    Select-Object -First 1 Name, LastWriteTime
```

<img width="716" height="259" alt="image" src="https://github.com/user-attachments/assets/fc4e950f-1d06-4bc0-bf63-7836d66f33ab" />

---

### Count Hidden Files

```powershell
($file | Where-Object Attributes -like "*Hidden*").Count
```

<img width="585" height="40" alt="image" src="https://github.com/user-attachments/assets/689d30a4-30ec-46d5-b1b8-3bfc1d4926fa" />

---

### Review Hidden Files

```powershell
$file |
    Where-Object Attributes -like "*Hidden*"
```

<img width="779" height="270" alt="image" src="https://github.com/user-attachments/assets/2b7969ed-a44b-4342-bdb5-c567229f8419" />

---

### Identify Largest Hidden Files

```powershell
$file |
    Where-Object Attributes -like "*Hidden*" |
    Sort-Object Length -Descending |
    Select-Object -First 5 Name, Length
```

<img width="466" height="209" alt="image" src="https://github.com/user-attachments/assets/844dd747-bdb6-4b63-abe1-aebccbea7c46" />

---

### Identify Oldest Files

```powershell
$file |
    Sort-Object LastWriteTime |
    Select-Object -First 5 Name, LastWriteTime
```

<img width="520" height="197" alt="image" src="https://github.com/user-attachments/assets/bd7236a0-203b-481c-b2b0-30b177424960" />

---

### Largest Non-Executable Files

```powershell
$file |
    Where-Object Extension -ne ".exe" |
    Sort-Object Length -Descending |
    Select-Object -First 5 Name, Length
```

<img width="621" height="219" alt="image" src="https://github.com/user-attachments/assets/559750fe-9c1b-4eb8-b24c-9ece757b031e" />



---

## 📊 Investigation Results

### Total Files

```text
175 Files
```

### Executable Files

```text
27 Executable Files
```

### Hidden Files

```text
9 Hidden Files
```

---

### Largest Files

| File | Size |
|--------|--------|
| Windows.iso | 4.89 GB |
| CitrixWorkspaceFullInstaller.exe | 850 MB |
| CitrixWorkspaceApp.exe | 501 MB |
| CitrixWorkspaceApp (1).exe | 407 MB |
| Microsoft.WebView2.FixedVersionRuntime.143.0.3650.66.x64.cab | 275 MB |

#### Observation

The largest file identified was:

```text
Windows.iso
```

at approximately:

```text
4.89 GB
```

This appears to be legitimate Windows installation media.

---

### Largest Executables

| File | Size |
|--------|--------|
| CitrixWorkspaceFullInstaller.exe | 850 MB |
| CitrixWorkspaceApp.exe | 501 MB |
| CitrixWorkspaceApp (1).exe | 407 MB |
| TeamViewer_Setup_x64.exe | 84 MB |
| voxpro5_2_0_1_setup.exe | 49 MB |

#### Observation

The executable files appear to be associated with:

- Citrix Workspace
- TeamViewer
- VoxPro
- Administrative software
- Productivity tooling

No obviously suspicious executable names were identified.

---

### Newest Executable

```text
BCUninstaller_6.2.0_setup.exe
```

Modified:

```text
July 22, 2026
```

#### Observation

The filename appears consistent with Bulk Crap Uninstaller (BCUninstaller), a legitimate software removal utility commonly used by technical users and administrators.

---

### Hidden Files

The largest hidden files identified were:

| File | Size |
|--------|--------|
| ~WRL1962.tmp | 88 KB |
| ~WRL0284.tmp | 34 KB |
| ~WRL3265.tmp | 33 KB |
| ~WRL0005.tmp | 21 KB |
| desktop.ini | 282 B |

#### Observation

The hidden files appear to be:

- Temporary application files
- Microsoft Office lock files
- Standard Windows configuration files

No hidden executable files or unusually large hidden files were identified.

---

### Oldest Files

| File | Modified |
|--------|--------|
| ~WRL0284.tmp | July 15, 2024 |
| ~$itical Thinking Touchstone 4.docx | July 17, 2024 |
| ~WRL3265.tmp | July 20, 2024 |
| ~WRL0005.tmp | September 24, 2025 |
| ~$ble labels WOA.docx | September 25, 2025 |

#### Observation

While most files in the Downloads folder are relatively recent, several hidden temporary files date back to 2024.

This indicates the Downloads directory contains remnants of historical activity and was not completely reset.

---

### Largest Non-Executable Files

| File | Size |
|--------|--------|
| Windows.iso | 4.89 GB |
| Microsoft.WebView2.FixedVersionRuntime.143.0.3650.66.x64.cab | 275 MB |
| SysinternalsSuite.zip | 193 MB |
| TeamViewer_MSI64.zip | 145 MB |
| TeamViewer_MSI64 (1).zip | 145 MB |

#### Observation

The presence of:

```text
SysinternalsSuite.zip
```

is noteworthy because Sysinternals tools are commonly used by administrators, security analysts, incident responders, and threat hunters when performing host investigations.

---

## 🧠 Analyst Assessment

### Observations

- The Downloads directory contained 175 files.
- 27 executable files were present.
- 9 hidden files were identified.
- The largest file was a Windows installation image.
- The newest executable was BCUninstaller.
- Hidden files consisted primarily of Office lock files, temporary files, and Windows configuration artifacts.
- No hidden executables were discovered.
- No obviously suspicious filenames were identified.

### Software Observed

Examples of software and administrative utilities identified during the investigation included:

```text
Citrix Workspace
TeamViewer
Audacity
Microsoft WebView2
Sysinternals Suite
VoxPro
```

These applications appear consistent with a workstation used for technical support, administration, and broadcast operations.

---

## 🔍 Conclusion

Based on:

- File size analysis
- Executable inventory
- Hidden file review
- File age analysis
- File extension review

No immediately suspicious artifacts were identified during the investigation. Additional investigation would only be warranted if:

- A specific IOC was provided.
- A suspicious filename was identified.
- A timeline-based investigation was required.
- Process or network activity suggested a compromised file.

---

## 🧠 What I Learned

- Applied file discovery and filtering techniques during an investigation.
- Used sorting and filtering to prioritize review efforts.
- Identified and analyzed executable files.
- Reviewed hidden artifacts and file attributes.
- Practiced documenting evidence and supporting observations.
- Learned how to develop an evidence-based analyst assessment.
