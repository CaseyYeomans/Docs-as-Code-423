# SurviveMatchGroup

The SurviveMatchGroup activity requests survivorship to be run on a specific match group via a workflow.

| | | |
| --- | --- | --- |
| **SurviveMatchGroup In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| StrategyName\* | String | The name of the matching strategy that defines the survivorship rules to be executed. |
| MatchGroup\* | String | The match group on which survivorship should be performed. |
| WaitTimeout | TimeSpan | The maximum time to server process should wait for any locks on the matching index to be released before abandoning the request. |
| **SurviveMatchGroup****Out Arguments** | | |
| MasterCodeByMatchGroup | Dictionary<string, string> | A Dictionary<string,string> that identifies the master code for each group supplied |
| OperationResult | MaestroOperationResult | Identifies the success or failure of the operation. Refer to the Errors collection for details of any service errors occurring when the request was processed. |

*\*Argument is required*

### Remarks

- Since SurviveMatchGroup sends a singular group for survivorship, the MasterCodesByMatchGroup dictionaryhas at most 1 entry.
- If the StrategyName provided does not exist, the running workflow instance is suspended.
- If the MatchGroup provided does not exist, it is not set to any survivorship whether the workflow instance status is completed or not.

### See Also

- [Survive Match Groups](https://support.profisee.com/wikis/profiseeplatform/survive_match_groups)