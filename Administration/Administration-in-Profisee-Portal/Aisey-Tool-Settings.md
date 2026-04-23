# Aisey Tool Settings

You can control how Aisey behaves when it wants to use a tool — giving you more transparency and control over actions taken on your behalf.

---

## How to Access

Click the **gear icon (⚙️)** in the bottom-left corner of the Aisey chat panel to open **Tool Settings**.

---

## What Are Tools?

Aisey uses tools to take actions within Profisee on your behalf — such as creating records, generating filter expressions, or retrieving entity details. Tool Settings lets you decide how each tool is permitted to run.

---

## Tool Behavior Options

Each tool can be configured with one of three behaviors:

| **Setting** | **Description** |
| --- | --- |
| **Always Run** | Aisey runs the tool automatically without interruption. Best for low-risk, read-only, or frequently used actions. |
| **Needs Approval** | Aisey pauses before running the tool and asks for your confirmation. Use this when you want visibility into actions before they are executed. |
| **Blocked** | Aisey is prevented from using the tool entirely. Use this to restrict actions you never want Aisey to perform. |

---

## Data Modification Warning

Some tools are marked with a **warning icon (⚠️)**. This indicates that the tool modifies or deletes data in Profisee. These tools default to **Needs Approval** to ensure you can review before any changes are made.

The following tools carry this warning:

* **Delete Attribute**
* **Delete Data Quality Rules**
* **Delete Entity**

---

## Notes

* Tool Settings are applied per user and do not affect other members of your organization.
* Default settings are pre-configured based on the risk level of each tool, but can be adjusted at any time.
* Changes take effect immediately — no save or refresh required.

---