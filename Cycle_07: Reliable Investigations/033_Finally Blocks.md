# 🛡️ Finally Blocks and Cleanup

**Badges**
- PowerShell 7+
- Difficulty: Beginner
- Category: Reliable Investigations
- Security: Error Handling
- Concept: Finally Blocks

---

## 📌 Executive Summary

This lesson introduced the `finally` block and demonstrated how PowerShell can execute specific actions regardless of whether a command succeeds or fails. By combining `try`, `catch`, and `finally`, scripts become more reliable and provide consistent feedback during investigations.

The `finally` block is commonly used to provide status notifications, perform cleanup tasks, complete logging activities, and ensure investigation workflows reach a predictable conclusion.

---

## 🎯 Learning Objective

Learn how to use `finally` blocks to guarantee that specific actions occur regardless of the success or failure of a PowerShell command.

---

## 🔐 Cybersecurity Application

Security investigations frequently encounter:

- Missing processes
- Missing services
- Deleted files
- Permission restrictions
- Incomplete datasets

Even when one stage of an investigation fails, analysts still need to know:

- The script completed execution
- Evidence collection reached its conclusion
- Cleanup tasks were performed
- Status information was recorded

The `finally` block helps ensure those activities always occur.

---

## ✅ Key Takeaways

- `finally` always executes.
- `finally` runs after the `try` and `catch` blocks.
- Investigation status messages are commonly placed inside `finally`.
- Cleanup tasks should occur regardless of success or failure.
- Reliable scripts provide predictable output.
- Error handling and cleanup often work together.

---

## 💻 PowerShell Commands

### Basic Try/Catch/Finally Structure

```powershell
try {

    Get-Process explorer -ErrorAction Stop

}
catch {

    "Process not found"

}
finally {

    "Investigation complete"

}
```

<img width="677" height="282" alt="image" src="https://github.com/user-attachments/assets/b5286dd8-c20d-4ac8-b430-87a87b66f441" />


---

### Missing Process Example

```powershell
try {

    Get-Process FakeProcess -ErrorAction Stop

}
catch {

    "Process not found"

}
finally {

    "Investigation complete"

}
```

Output:

```text
Process not found

Investigation complete
```

<img width="594" height="212" alt="image" src="https://github.com/user-attachments/assets/5864987a-5852-4590-9194-ed264ca8011d" />


---

### Service Investigation Example

```powershell
try {

    Get-Service WinRM -ErrorAction Stop

}
catch {

    "Service not found"

}
finally {

    "Service investigation completed"

}
```

<img width="471" height="232" alt="image" src="https://github.com/user-attachments/assets/a7bb8744-5904-474a-b07e-4af1955ffede" />


---

### Reliable Service Investigation Function

```powershell
function Get-ServiceInfo {

    Param(
        $Name
    )

    try {

        Get-Service $Name -ErrorAction Stop

    }
    catch {

        "Service not found"

    }
    finally {

        "Investigation complete"

    }

}
```

<img width="680" height="487" alt="image" src="https://github.com/user-attachments/assets/c5ed59fc-4875-4431-956c-ff8ec117f85a" />


---

## 🧠 What I Learned

- Learned how the `finally` block works.
- Learned how `finally` interacts with `try` and `catch`.
- Learned that cleanup activities should not depend on successful execution.
- Improved understanding of script reliability.
- Learned how to build more professional investigation tools.
- Gained a better understanding of predictable script execution.

---

## 🔍 Investigation Notes

### Understanding Script Flow

PowerShell executes Try/Catch/Finally using the following workflow:

```text
Try
↓
Catch (if needed)
↓
Finally
```

Regardless of success or failure, the script eventually reaches the `finally` block.

---

### Investigation Completion Notification

One of the most useful applications of a `finally` block is providing a completion message.

Example:

```text
Investigation complete
```

This allows analysts to know execution reached the end of the workflow, even if part of the investigation failed.

---

### Cleanup Operations

The `finally` block is commonly used for:

- Investigation status notifications
- Logging activities
- Export verification
- Temporary file cleanup
- Resource release
- Final report generation

These activities should happen whether or not the investigation encounters an error.

---

### Reliable Investigation Tools

Without a `finally` block:

```text
A script may stop unexpectedly and leave the user uncertain whether execution completed.
```

With a `finally` block:

```text
The script always provides a predictable ending.
```

This makes troubleshooting and reporting significantly easier.

---

## 🧠 Analyst Reflection

Errors are not always avoidable during investigations.

Processes terminate.

Services disappear.

Files are deleted.

Permissions change.

A reliable investigation tool must be prepared for these situations.

The `finally` block provides a consistent location for cleanup and status reporting, ensuring the investigator always receives confirmation that the workflow reached completion.

Although the `try` block may succeed and the `catch` block may handle errors, the `finally` block acts as the final checkpoint in the investigation process. This makes scripts easier to trust, troubleshoot, and maintain.

By combining:

```powershell
try
catch
finally
```

PowerShell scripts become more resilient and more suitable for real-world cybersecurity investigations.
