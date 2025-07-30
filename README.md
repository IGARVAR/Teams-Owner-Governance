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
- Microsoft Teams PowerShell Module  
- Valid SMTP relay/server for `Send-MailMessage`  
- Read access to Microsoft Teams ownership data  
- Admin permissions (or delegated rights) to enumerate Teams and owners

---

## 🧪 Usage

1. Clone or download the repo  
2. Prepare credentials with:
   ```powershell
   Get-Credential | Export-CliXml -Path "$env:USERPROFILE\SRV_MsTeamsConfig.Cred"
   ```
3. Review and update config values inside `01_ConfigAndConnect.ps1`
4. Run the master script:
   ```powershell
   .\Run_TeamsNotifyJob.ps1
   ```

---

## 🧩 Modular Breakdown

`01_ConfigAndConnect.ps1` – Loads parameters and connects to Teams

`02_GetTeamsAndOwners.ps1` – Retrieves all Teams and their owners

`03_PreviewAndExport.ps1` – (Optional) exports single-owner Teams for review

`04_SendNotifications.ps1` – Sends personalized email alerts to owners

`05_ReportToSelf.ps1` – Sends a summary report with log and stats

`Run_TeamsNotifyJob.ps1` – Master script that runs all steps sequentially
