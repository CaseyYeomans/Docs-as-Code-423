# ProcessMatchingStrategy

The ProcessMatchingStrategy activity allows a designer to build a workflow that executes a matching strategy using the supplied StrategyName.

| | | |
| --- | --- | --- |
| **ProcessMatchingStrategy In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Action\* | ProcessAction | Identifies the how the strategy should be run. See below for options. |
| StrategyName\* | String | The name of the strategy to run. |
| RunSync | Boolean | A boolean value indicating if the activity will wait for the strategy to finish or whether the server will process the strategy asynchronously. |
| **ProcessMatchingStrategy Out Arguments** | | |
| OperationResult | MaestroOperationResult | Indicates the results of the strategy execution. |

*\*Argument is required*

### Remarks

The workflow instance is suspended if the StrategyName provided does not exist.

**Option for ProcessMatchingStrategy:**

- 0 - Cancel
- 1 - ClearAllPriorResults
- 2 - ClearPriorResults
- 3 - ClearPriorResultsExcludeUserMapped
- 4 - ClearPriorResultsExcludeApproved
- 5 - ClearMatchingResults
- 6 - IncludeSurvivorship
- 7 - IndexUnload
- 8 - IndexAddNew
- 9 - IndexAddOrUpdate
- 10 - IndexFullRebuild
- 11 - IndexOnly
- 12 - SurvivorshipOnly

### See Also

- [Match Record](http://support.profisee.com/wikis/profiseeplatform/match_member_activity)