# LogMessage

The LogMessage activity writes a message to the log.

| | | |
| --- | --- | --- |
| **LogMessage In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Message\* | String | Allows data other than the member that triggered the workflow to be passed to the workflow. |
| LogType\* | EventLogEntryType | Indicates the type of message to be logged. |
| **LogMessage Out Arguments** | | |
| Result | | Result description. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

Workflows initiated manually or via eventing cannot use the message object. This functionality is restricted to programmatic instantiation via a web service call.

###