# Notion to Slack & Google Sheets Automation

This project automates your workflow. It monitors a Notion database and notifies you on Slack when a task is finished, while keeping a clean history in Google Sheets.

## 📝 What this Automation Does

This tool specifically looks for any task in Notion that is marked as **"Done."** 

When a task reaches "Done" status, the automation:
1.  **Checks for Duplicates:** It first checks Google Sheets to see if this task was already recorded. This prevents the same task from being logged twice.
2.  **Sends a Slack Alert:** If it's a new "Done" task, it sends a neat message to your Slack channel.
3.  **Logs to Google Sheets:** It then adds the task details (Title, Owner, and Time) to your spreadsheet for your records.

## ⚙️ How it Works 

-   **The Trigger:** It watches your Notion "Requests" database for any updates.
-   **The Gatekeeper:** A filter only lets tasks through if they are exactly set to "Done."
-   **The Protection:** It searches your spreadsheet first. If the task is already there, it stops (to avoid duplicate entries).
-   **Error Prevention:** If a Notion field is accidentally left blank, the automation won't crash. It will just use a default name like "(No title)" or "(Unassigned)."

## 📁 What's in this Folder?

| File | What is it? |
|------|-------------|
| `blueprint.json` | The "brain" of the automation. You can import this into Make.com to set it up instantly. |
| `Automation_Log_Headers.csv` | A template showing how to set up your Google Sheet columns. |
| `README.md` | This simple guide. |

## 🛠 Easy Setup Guide

1.  **Spreadsheet:** Create a Google Sheet and name your columns using the [template provided](./Automation_Log_Headers.csv).
2.  **Make.com:** Create a new scenario and select **"Import Blueprint"** to upload the `blueprint.json` file.
3.  **Connect Your Apps:** Click on each module (Notion, Slack, Google Sheets) to sign in to your accounts.
4.  **Turn it On:** Save and click "Run Once" or set it to run automatically!


