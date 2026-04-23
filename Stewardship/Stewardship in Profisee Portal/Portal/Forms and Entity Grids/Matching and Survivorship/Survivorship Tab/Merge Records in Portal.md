# Merge Records in FastApps Portal

The Merge function allows for the consolidation and removal of duplicate records in a single source system. After configuring a matching strategy and bringing the results together in a match cluster, the merge process gives you an opportunity to review the records, pick the best one, and remove the rest. The result is much cleaner data in your golden record data hub and in the external systems that support the merge process.

Controls used:

| | |
| --- | --- |
| | **Merge** |
| | **Merge Winner** |

## Merge Considerations

Keep the following in mind when reviewing Merge candidate records:

- Merge functions can only be performed on records from one external system at a time. A match cluster may contain records from multiple external systems--for example, from Salesforce and Dynamics CRM. Multiple merge operations are required to complete the merge process across both external systems.
- For a record to be considered a merge candidate, the record must have a non-null SAIM ID from one or more external systems. The SAIM ID must be associated with the external system to which the merge status is linked.
- The SAIM IDs must be associated with external systems configured to support merge.
- The record must not have been merged or "consolidated out" already. Its Merge Parent attribute along with its various external system Merge Status attributes must be NULL.
- If a record has already been merged, it will still be visible in the match cluster; however, it will be removed from consideration in subsequent merges.

## Performing Merge

1. Open the desired match cluster.
2. Select any match record (not the golden record). The golden record cannot be merged, and is not considered a merge candidate. The selected record must be a merge candidate.
3. Click the **Merge**button on the Record Source card you wish to merge. The cluster filters all cards of that same Record Source to a golden record and the cluster of merge candidates associated with the currently selected record. If the cluster has a golden record, it is not selectable.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7dc0fbf25ade288a.png)
4. Click the trophy icon next to the record you want to be the winning record. The losing records' merge parent attributes are changed to refer to the ID of the winning record and their merge status is changed to 10 [Merge Pending]. In addition a Merge Confirmation window opens to allow the user to confirm they understand the impact of performing the merge operation.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idbc0b9fb4e54303a.png)
5. Click the acknowledgment checkbox. Once checked, this checkbox will remain checked for the duration of the the user's session.
6. Click **Yes**. The merge operation completes. The winning record is labeled **Merge Winner**. The others are labeled **Merge Loser**.

The grid remains in Merge mode until the Merge toggle is released. After exiting Merge mode, the merge candidates remain visible in the match cluster. When all merge operations have been completed for an external system, the Merge option is disabled when records from that system are selected. If the Merge option is still available, other potential Merge possibilities are still available for the selected record.