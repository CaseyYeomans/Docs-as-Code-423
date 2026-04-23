# MatchRecord

The MatchRecord activity allows a designer to match a specified record to a match group based on a previously configured matching strategy or override matching strategy.

| | | |
| --- | --- | --- |
| **MatchRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | The RecordDataContext object. |
| OverrideStrategyName | String | The strategy name to use to apply the match. This allows the workflow to dynamically adjust the strategy based on information the activity has at runtime. |
| WaitTimeout | TimeSpan | The maximum time to wait for a response in case another process has the matching index locked. |
| **MatchRecord Out Arguments** | | |
| ResultStatus | MatchStatus | The MatchStatus value that indicates the resulting status of the match. |
| Errors | Collection<Error> | A Collection<Error> object that lists any errors that occurred during activity execution. |
| MatchClusterId | String | The ID of the group to which the record matches, or a new group if the record is determined to be unique. |
| MatchScore | Double | The score the record has within the group. |
| MatchRecordCode | String | The Code of the record to which the source record matched when being accepted to the match group. |

*\*Argument is required*

### Remarks

To perform the MatchRecord activity, it is recommended to have an existing matching index (through ProcessMatchingStrategy) prior to execution. Otherwise, this activity will not match the record.

### See Also

- [ProcessMatchingStrategy](https://support.profisee.com/wikis/profiseeplatform/process_matching_strategy)
- [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)