---
description: Explain how to set up and monitor StackSync AI Connector in StackBuilder.
title: StackSync AI Connector
read_time: 4 min read
customFields:
 ai_index: true
 audience: 
  - developer
---

# StackSync AI Connector

## Overview
The StackSync AI Connector automatically synchronizes configuration changes from appStack to Cloud2Code.
Unlike the legacy direct-sync process, this connector uses an asynchronous webhook trigger to process updates more efficiently and reduce reliance on manual refresh cycles.
As part of the StackBuilder workflow, the connector enables users to monitor and trigger synchronization events from a single interface.

> [!IMPORTANT] 
> Starting with release vNEXT, the manual sync button label in the StackBuilder UI has changed from Sync Now to Run AI Sync.

## Installation and Usage

**Prerequisites**

1. You must have an active **Cloud2Code** account.
2. You need permissions to view and edit configurations in appStack.
3. Use StackBuilder version `vNEXT` or later.

## Step-by-step instructions

1. **Enable the Connector**
- In **StackBuilder**, go to **Integrations > Connectors**.
- Find **StackSync AI Connector** and select **Enable**.

2. **Configure the Webhook Trigger**
- The connector listens for asynchronous triggers from appStack.
- Make sure your appStack instance has outbound [webhook](https://stackoverflow.com/tags/webhooks/info) permissions.
```
  {
  "webhook": {
    "target": "https://api.cloud2code.io/stacksync/webhook",
    "method": "POST",
    "events": ["config.update"]
   }
 }
```

3. **Run a Manual Sync**
- In StackBuilder, select **Run AI** Sync to start a manual synchronization.
- StackBuilder displays the sync status and any detected metadata issues.

4. **Monitor Sync Progress**
- Use **StackBuilder > Activity** to monitor sync progress and review events.
- _(Note: Log file locations are not documented yet.)_

> [!Tip] 
> See the [Cloud2Code metadata documentation]() for valid field structures and examples.

## Try It Out

You can manually import configuration data from **appStack** into **Cloud2Code** by using the **StackSync AI Connector**.
This helps you test the webhook configuration or verify metadata integrity.

```
cloud2code import \
  --source appstack://<your_project_id> \
  --connector stacksync-ai \
  --metadata ./path/to/<metadata_file>.json \
  --cluster <cluster_name> \
  --async true \
  --token <your_api_token>
```

### Example
```
cloud2code import --source appstack://stack-ai-dev --connector stacksync-ai --metadata ./config/metadata.json --cluster prod-cluster --async true --token 
```

|  Parameters | Description |
| --- | --- |
| `<your_project_id>` | The appStack project identifier |
| `<metadata_file>.json` | The metadata file containing AI configuration |
| `<cluster_name>` | The target Cloud2Code cluster for deployment |
| `<your_api_token>` | Your authentication token for Cloud2Code API access |

## Troubleshooting

### Common errors

**1. Metadata errors:**
- If the `metadata.json` file is missing **ai_index** or **clusters**, the sync will fail.
- Ensure these fields are present before you start the sync.

**2. Sync failures:**
- Verify webhook is correctly configured and reachable from **appStack** to **Cloud2Code**.
- Check StackBuilder for sync status; delays may occur due to async triggers.

**3. Unknown Logging Location**
- Sync operation logs are not available yet.
- As a workaround, check **StackBuilder activity logs** or Cloud2Code change history for any errors.

## References
 - **[Cloud2Code]()**
 - **[StackBuilder Integration Overview]()**
 - **[appStack Webhook Setup]()**
