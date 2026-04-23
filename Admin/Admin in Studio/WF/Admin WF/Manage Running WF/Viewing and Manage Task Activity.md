# Viewing and Managing Task Activity

## Forcing Tasks to Complete

Forcing a task to complete can be useful when testing or troubleshooting a workflow. It simulates an approval or rejection for an Approve task, or a contribution for a Contribute task. You can also [force a task to expire](https://support.profisee.com/wikis/profiseeplatform/force_a_task_to_expire). No data is changed, and no user involvement is necessary.

There are three different ways to force a task to complete:

- **Force complete**

Simulates a contribution by a participant, although no changes are made to member data. When a task is forced to complete, it is removed from the participants' task lists.

The forced completion satisfies the requirement for the workflow task for participant input, and the workflow then moves to the next task, sending notifications to the configured participants. Force complete applies only to Contribute tasks.
- **Force approve**

Simulates an approval by a participant, although no changes are made to member data.

The forced approval satisfies the Approve task requirement for participant input. If the administrator is not a member of the tasks participant group, the administrator has a task assignment created and then flagged as having approved the task.The workflow then moves to the next activity in the workflow, sending notifications to the configured participants. Force approve applies only to Approve tasks. A forced approval overrides the configured Approvals Required setting if the task calls for more than one approval.
- **Force reject**

Simulates a rejection by a participant, although no changes are made to member data. When a task is forced to end as if rejected by a participant, the tasks for the Approve task are removed from the participants' task lists.

A forced approval or rejection satisfies the Approve task requirement for participant input. The workflow then moves to the next activity in the workflow, or ends if the forced task was the last task in the workflow. Force approve and Force reject apply only to Approve tasks.

To force a task to complete:

The status for the task in the list changes to Complete.

1. Open Workflow Administration and [view the open tasks](https://support.profisee.com/wikis/profiseeplatform/view_workflow_tasks).
2. Select an open task in the list.
3. Do one of the following:

- For a Contribute Task, click **Force Complete** in the Tasks toolbar, or right-click the selected task and click **Force Complete** on the menu.

**--or--**

1. For an Approve Task, click **Force Complete** in the Tasks toolbar, or right-click the selected task and click **Force Complete** on the menu.
2. On the menu, click **Approve** or **Reject**.

## Forcing Tasks to Expire

Tasks normally expire when participants do not respond within the Maximum Duration configured for that task. It may be necessary to force a task to expire manually, without user interaction, as when testing a new workflow.

Forcing a task to expire simulates a task reaching the time configured for the task maximum duration and ending due to inaction by the participants. When a task is forced to expire, the task is removed from the participants' task lists. The workflow continues to the next activity. If the task is the last task in the workflow, then the workflow ends.

To force a task to expire:

1. Open Workflow Administration and [view the open tasks](https://profisee.magentrixcloud.com/wikis/profiseeplatform_v7/view_workflow_tasks).
2. Select an open task in the list.
3. Click **Force Expire** in the toolbar, or right-click the task and then click **Force Expire** on the menu.

You can also right-click the task and then click **Force Expire** on the menu.

The task expires. The status for the task in the list changes to Expired.