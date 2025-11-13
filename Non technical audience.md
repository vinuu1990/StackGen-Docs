# StackSync AI Connector

## Overview
The StackSync AI Connector helps you keep your appStack settings up to date in Cloud2Code automatically.
Whenever you make changes in appStack, the connector sends those updates to Cloud2Code so your setup stays in sync. You can also start a sync manually whenever you need to.
This connector is available in StackBuilder, where you can see when the last sync happened, start a new one, and check the results.

> **What’s new:** The button name has changed from **Sync Now** to **Run AI Sync** in the latest release.

## Uses
 - Keeps your Cloud2Code setup aligned with appStack automatically. 
 - Reduces manual work and sync errors. 
 - Lets you monitor syncs in one place — StackBuilder.

## Installation and Usage
You only need to set up the connector once. After that, it works automatically in the background whenever appStack updates occur.

### **Before you start**
Make sure you have:

1. Access to your **Cloud2Code** account.
2. Access to your appStack project.
3. The latest version of StackBuilder `vNEXT` or later.

## Step-by-step instructions

**Step 1: Turn On the Connector**
- Open **StackBuilder**. 
- Go to **Integrations > Connectors**.
- Find **StackSync AI Connector** and select **Enable**.

> Once you enable it, the connector starts listening for updates from appStack.

**Step 2: Sync Your Data**
You can let the connector sync automatically, or you can do it yourself:
- In **StackBuilder**, go to your project.
- Select **Run AI Sync** to start the sync manually.
- Wait for the process to finish — you’ll see the sync status right in the StackBuilder screen.


**Step 3: Check Your Sync**
After the sync, check your project in Cloud2Code to make sure your appStack changes are applied. You can also view sync activity in StackBuilder.

> Note: Connector logs are not available yet, but StackBuilder still shows the sync results and basic status information.


## Troubleshooting

| Issue | What It Means | How to Fix It |
| ---- | ---- | ---- |
| **Sync didn’t happen**           | The connector didn’t receive updates from appStack.              | Make sure your appStack project is set up to send updates and that the connector is turned on in StackBuilder. |
| **Error: missing ai_index**      | Some required information is missing in your configuration file. | Re-export your appStack project or ask your admin to update the metadata file so it includes `ai_index`.       |
| **Error: missing clusters**      | The connector can’t find the list of clusters to update.         | Make sure your metadata file includes a `clusters` list. Contact your admin if needed.                         |
| **Button still says “Sync Now”** | You are using an older version of StackBuilder.                  | Update to the latest version to see **Run AI Sync**.                                                           |

## Quick Tips

- After starting a sync, check **StackBuilder > Activity** to see if it completed successfully.
- Most sync problems are caused by missing information in the metadata file. If you see an error, confirm that your project’s metadata is complete.
- You don’t need to touch the webhook settings — the connector handles them automatically once it’s enabled.

> **Tip:** If you’re unsure about a missing field, your admin or someone with Cloud2Code access can help you check or update the metadata.



## References
 - **[Cloud2Code]()**
 - **[StackBuilder Integration Overview]()**
 - **[appStack Webhook Setup]()**
