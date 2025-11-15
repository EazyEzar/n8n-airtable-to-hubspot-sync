# n8n: Batch-Sync Approved Leads from Airtable to HubSpot

This n8n workflow provides a robust, batch-processing solution for syncing approved leads from an Airtable "control panel" directly into HubSpot.

It automatically **Finds or Creates** companies, **Creates or Updates** contacts, and **Associates** them correctly, with full error-logging back to Airtable.

**View this template on the n8n Creators Hub:** [Link to your template] *(<-- Add this link once it's published!)*

---

## What it Does
This workflow runs on a schedule (e.g., every 5 minutes) to find leads in an Airtable view named **'👍 Ready to Sync'**. It then processes them in a batch, one by one.

### 1. Before: New Leads Arrive
Your Airtable base has new leads with a **'📥 New Lead'** status.

<img width="1916" height="622" alt="Screenshot 2025-11-15 110214" src="https://github.com/user-attachments/assets/7d0a912d-2c07-4120-9f52-0202c8fd7893" />

### 2. The Trigger: A Human Approves the Lead
You (or a teammate) manually review a lead and change their status to **'👍 Ready to Sync'**.

<img width="1916" height="612" alt="Screenshot 2025-11-15 110325" src="https://github.com/user-attachments/assets/fa16ad33-50c6-4019-9e3e-a753b550a308" />

### 3. The Workflow Runs (The Magic)
n8n fetches all leads in that view (up to 50 at a time) and loops through them. For each lead, it:
* Finds (or creates) a **Company** in HubSpot based on the email domain.
* Creates (or updates) a **Contact** in HubSpot based on the email.
* Automatically **associates** that Contact with that Company.

### 4. After: The 2-Way Sync is Complete
The workflow automatically updates the *same* Airtable row with the new HubSpot IDs and a **'✅ Synced'** status. If an error occurs, it posts the error message in the 'Note' field.

<img width="1908" height="612" alt="Screenshot 2025-11-15 110358" src="https://github.com/user-attachments/assets/2ce73fbd-233d-4ffd-85ee-c00e39d1733b" />

## How to Use this Repository

1.  **Download the Workflow:**
    * Click the `Airtable to HubSpot v4.0.json` file in this repository.
    * Click the **"Raw"** button.
    * Right-click and "Save As..." to download the JSON file.
2.  **Import to n8n:**
    * In your n8n instance, go to "Workflows" and click **"Import"** -> **"Import from File"**.
    * Upload the JSON file you just downloaded.
3.  **Follow the Setup Guide** in the description below or in the sticky notes inside the workflow.

## Full Setup Guide

Setup should take less than 10 minutes.

### 1. Copy the Airtable Base (Mandatory)
This is a mandatory first step! You must use this template base, as the workflow is built for its specific fields and views.
* ➡️ **[Click Here to Copy the Base Template](https://airtable.com/appthZgrzxKzQPEYa/shrRoRtIXoL1tlDVv)**
* (First time using Airtable? [Sign up here with my link](https://airtable.com/invite/r/Isr7G94S))

### 2. Add Your n8n Credentials
* [How to connect Airtable to n8n (Video)](https://www.youtube.com/watch?v=xFFfkBeI2rQ)
* [How to connect HubSpot to n8n (Video)](https://www.youtube.com/watch?v=KzP52kRsRrk)

### 3. Configure 3 Nodes in n8n
* `Schedule Trigger`: Set how often you want it to run (e.g., every 5 minutes).
* `get 👍Ready to Sync`: Select your Airtable credential and the Base you copied.
* `Search company`: Select your HubSpot credential.

### 4. Activate!
Save and activate the workflow. To test it, just change a lead's 'Status' in Airtable to **'👍 Ready to Sync'**.

## Requirements
* An **Airtable** account.
* A **HubSpot** account (a free developer sandbox account is recommended for testing).
* n8n credentials for both Airtable and HubSpot (using a Private App Token for HubSpot).
