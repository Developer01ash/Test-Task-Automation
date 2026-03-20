# Notion Status Automation - Test Task Submission

This repository contains the complete solution for the Automation Engineer (Contract) test task. The project automates Notion status updates, notifying Slack and logging events in Google Sheets with built-in duplicate protection.

## 📝 Solution Description (5–10 sentences)

This automation uses a Notion "Watch Database Items" trigger configured for record updates in the "Requests" database. A filter ensures only entries with the status **"Done"** pass to the core logic. To prevent duplicate entries, the scenario first searches the Google Sheets "Automation Log" for existing rows with the same record Title and Status. A **Router** then branches the flow: if no matching log is found (New Entry), it sends a formatted message to Slack and adds a new row to Google Sheets. If a duplicate exists, the scenario gracefully skips the actions, ensuring the log remains clean. All field mappings use `ifempty()` logic to safely handle any missing data in Notion properties.

## ⚙️ How it Works (Logic & Validations)

-   **Trigger:** Notion (Watching for updates in the 'Requests' database).
-   **Validation 1 (Filter):** Passes only records where `Status = Done`.
-   **Validation 2 (Duplicate Check):** Uses a Google Sheets search module to check for existing entries.
-   **Router Logic:** 
    -   **Route 1 (Not a Duplicate):** Sends Slack notification → Adds Google Sheets row.
    -   **Route 2 (Duplicate):** Stops processing (Duplicate detected).
-   **Handling Empty Fields:** Each mapping is protected with fallbacks (e.g., `{{ifempty(Title; "(No title)")}}`).

## 📁 Repository Contents

| File | Description |
|------|-------------|
| [blueprint.json](./blueprint.json) | The complete Make.com scenario export to be imported. |
| [Automation_Log_Headers.csv](./Automation_Log_Headers.csv) | Header template for the Google Sheets 'Automation Log' table. |
| [README.md](./README.md) | Full project documentation and submission summary. |

## 🛠 Setup & Maintenance

### Setup
1.  **Google Sheets:** Create a spreadsheet named "Automation Log" and import [Automation_Log_Headers.csv](./Automation_Log_Headers.csv).
2.  **Make.com:** Create a new scenario and **Import Blueprint** using [blueprint.json](./blueprint.json).
3.  **Connections:** Re-link your Notion, Slack, and Google accounts in each module.
4.  **Notion:** Ensure the "Requests" database is shared with your Notion integration.

### Maintenance
-   **Connections:** If any service stops working, check the "Connections" tab in Make.com.
-   **Database Fields:** If you rename a Notion property (e.g., change "Owner" to "Assignee"), you must update the mapping in the Slack and Google Sheets modules.
-   **Logs:** Monitor the "History" tab in Make.com for any failed executions or 4xx/5xx errors from APIs.

## 📈 Evaluation Criteria Check
-   [x] Works correctly
-   [x] Duplicate protection implemented
-   [x] Logic is clear and documented
-   [x] Empty fields are handled
-   [x] Slack format follows requirements

---
*Created for the Automation Engineer Contract Test Task.*
