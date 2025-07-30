# 🛡️ Teams Owner Governance Automation

This PowerShell-based automation scans Microsoft Teams for ownership gaps and sends notification emails to users who are sole owners of their teams. The goal is to **encourage the assignment of backup owners** to reduce the risk of inaccessible Teams in case of employee departure, vacation, or absence.

---

## 🚀 Features

- Detects all Teams with **only one owner**
- Sends **personalized HTML email reminders** to sole owners
- Supports multiple run modes:  
  - `ALL`: notify all discovered users  
  - `TEST`: send only to a test address  
  - `SELECT`: choose specific users from the discovery list
- Creates a **CSV log** with timestamps and delivery status
- Includes a clean and branded HTML email template
- Easy to extend, modular code layout

---

## 📸 Preview

> Example of the notification email body:

<img src="assets/email-preview.png" alt="Teams ownership alert email screenshot" width="600"/>

---

## 🧱 Requirements

- PowerShell 5.1+  
- Microsoft Graph PowerShell SDK (Teams module)  
- Valid SMTP relay/server for `Send-MailMessage`  
- Read access to Microsoft Teams ownership data  
- Admin permissions (or delegated rights) to enumerate Teams and owners

---

## 🧪 Usage

1. Clone or download the repo  
2. Open `Main.ps1` and set:
   - `$smtpServer`, `$sender`, `$testRecipient`, `$logOutput` paths  
3. Run the script:
   ```powershell
   .\Main.ps1

## 🧩 Modular Breakdown
01_GetTeams.ps1: Collects all Teams and their owners

02_AnalyzeTeams.ps1: Filters down to only single-owner Teams

03_NotifyOwners.ps1: Sends email notifications

04_ReportToSelf.ps1: Sends a summary report to admin

05_Main.ps1: Orchestrates the process (entry point)
