# WaitForEvent

When the WaitForEvent activity is reached within a workflow, a workflow bookmark is created and execution pauses until the bookmark is resumed.

| | | |
| --- | --- | --- |
| **GetMember In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Bookmark Name\* | String | A **string** representing where the workflow runtime will go idle and wait to be resumed. |
| **GetMember Out Arguments** | | |
| Result | T specified by the user | Set to the data associated with the bookmark resumption. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.