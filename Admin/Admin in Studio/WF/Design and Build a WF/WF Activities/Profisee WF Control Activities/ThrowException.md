# ThrowException

The ThrowException activity throws an exception of type T.

| | | |
| --- | --- | --- |
| **ThrowException In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Message\* | String | A **String** value containing the message that will be logged and thrown. |
| **ThrowException Out Arguments** | | |
| Result | String | The message that is logged and thrown from an exception of type T. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This activity throws an exception of type T specified by the user. From this exception, a message is logged and thrown.