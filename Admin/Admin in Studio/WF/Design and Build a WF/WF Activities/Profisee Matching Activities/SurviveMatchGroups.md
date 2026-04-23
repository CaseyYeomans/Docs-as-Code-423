# SurviveMatchGroups

The SurviveMatchGroups activity requests survivorship to be run on specific match groups via a workflow.

| | | |
| --- | --- | --- |
| **SurviveMatchGroups In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| StrategyName\* | String | The name of the matching strategy that defines the survivorship rules to be executed. |
| MatchGroups\* | CollectuibString | A Collection<string> that contains the match groups that should be subjected to survivorship processing. |
| WaitTimeout | TimeSpan | The maximum time to server process should wait for any locks on the matching index to be released before abandoning the request. |
| **SurviveMatchGroups****Out Arguments** | | |
| MasterCodeByMatchGroup | Dictionary<string, string> | A Dictionary<string,string> that identifies the master code for each group supplied |
| OperationResult | MaestroOperationResult | Identifies the success or failure of the operation. Refer to the Errors collection for details of any service errors occurring when the request was processed. |

*\*Argument is required*

### Remarks

- If the StrategyName provided does not exist, the running workflow instance is suspended
- If the MatchGroups provided do not exist, they are not set to any survivorship whether the workflow instance status is completed or not.

### See Also

- [Survive Match Group](https://support.profisee.com/wikis/profiseeplatform/survive_match_group)