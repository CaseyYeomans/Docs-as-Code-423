# LookUpRecord

The LookUpRecord activity takes in a **Record** object and returns that object's match details.

| | | |
| --- | --- | --- |
| **LookUpRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| StrategyName\* | string | A **string** representing the matching strategy to be used. |
| Record\* | [Record](http://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Record** object containing information of the specified Record that will be added. |
| IncludeMatchesInRecordGroups\* | bool | A **bool** that indicates whether matches will be included that are in record groups. |
| WaitTimeout | TimeSpan | A **TimeSpan** that sets the maximum allowed time for the process. If this is null then it will continue until the process is completed. |
| **LookUpRecord Out Arguments** | | |
| ResultStatus | MatchStatus | The **MatchStatus** of the record. |
| ResultScore | double | A **double** indicating the quality of the record match. If the record is unique ResultScore returns 0. |
| Errors | Collection<Error> | A **Collection<Error>** object that returns empty if the operation was successful. |
| LookUpResult | RecordMatchesResult | Returns the match details of the result of the lookup. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

If there is not a matching strategy associated with the StrategyName argument the user provided, then an exception will be thrown. If the given record does not have a match then the LookUpResult will be null, ResultStatus is set to NoStatus, and ResultScore will default to 0.

### See Also

- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)