# Impact on Workflows when Profisee Accounts are Deleted

When deleting users and teams from Profisee that are also participants in workflows, keep in mind the following potential impacts:

- Deleting users removes them from all workflow activities where they have task assignments.
- Deleted users are excluded from future task assignments when workflows are started.
- If a user in an active task is deleted, all task assignments in active workflows for that user (or team) end with a canceled status. If a deleted user or single user in a team is the only remaining user assigned to a task, the activity automatically expires when the final task is canceled.
- If a user is deleted from Profisee, that user will not be assigned to a task even when that user appears in a task participant override list provided by the workflow.

Override participants are identified by the workflow. Check workflows that perform dynamic task assignments periodically to ensure that deleted users are no longer included for such assignments. If a deleted user is the only user assigned to a task, the task assignment will fail, and the resulting task will automatically expire because no task could be created. This does not apply to teams because teams cannot be assigned as override participants.
- Outstanding notifications awaiting delivery to the deleted user through digest notifications are flagged as failed and are not sent.

See [Accounts overview](https://support.profisee.com/wikis/profiseeplatform/accounts_overview) and [Deleting Accounts](https://support.profisee.com/wikis/profiseeplatform/delete_accounts) for information on Profisee users.