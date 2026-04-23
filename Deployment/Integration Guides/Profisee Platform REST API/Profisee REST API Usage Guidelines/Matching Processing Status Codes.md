# Matching Processing Status Codes

The Matching API endpoint returns a processingStatus value for each matching strategy. The possible values are as follows:

| | |
| --- | --- |
| **Status** | **ID** |
| Idle | 0 |
| Initialized | 1 |
| ProcessClearing | 2 |
| ProcessPreparing | 3 |
| IndexLoading | 4 |
| IndexMapping | 5 |
| IndexPopulating | 6 |
| ProcessMatching | 7 |
| Publishing | 8 |
| ProcessSurvivorship | 9 |
| BusinessRules | 11 |
| PublishingSurvivorship | 12 |
| IndexLoadingAfterSurvivorship | 13 |
| IndexMappingAfterSurvivorship | 14 |
| IndexPopulatingAfterSurvivorship | 15 |
| BusinessRulesAfterMatching | 16 |
| BusinessRulesAfterSurvivorship | 17 |
| UpdatingMasterCounts | 18 |
| CleanupProcessMatching | 19 |
| CleanupPublishing | 20 |
| CleanupPreparing | 21 |
| IndexPreLoading | 22 |
| IndexPreLoadingAfterSurvivorship | 23 |
| PublishDomainMembers | 24 |
| IndexLoaded | 25 |
| Canceling | 97 |
| Finished | 98 |
| Canceled | 99 |
| Error | 100 |