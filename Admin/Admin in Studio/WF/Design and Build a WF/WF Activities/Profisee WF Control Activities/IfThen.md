# IfThen

The IfThen activity provides conditional statements.

| | | |
| --- | --- | --- |
| **IfThen In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Condition | C# type | A **Boolean** expression that is evaluated before the possible execution of the activities within the Then sequence. |

*\*Argument is required*

### Remarks

If the condition evaluates to True, the activities contained in the Then sequence are executed. Otherwise, the activities after the IfThen activity are executed. This activity allows multiple IfThen activities within each other, along with as many activities as are needed within the IfThen activity.

###