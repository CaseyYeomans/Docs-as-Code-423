# ExpireTask

The ExpireTask activity takes in a TaskId and expires the task with the corresponding TaskId.

| | | |
| --- | --- | --- |
| **GetMember In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| TaskId\* | MaestroIdentifier | A **MaestroIdentifier** object representing the task to be expired. |

*\*Argument is required*

### Remarks

If a task does not exist with the provided TaskId, an error will be logged and thrown.

###