# Error Handling for Staging Tables

## Writing Error Limit

The **Writing error limit** system setting defines how many errors can occur during bulk staging before processing automatically stops. If the error limit is reached, all members remain within the staging table. If the error is related to a violation of a data quality constraint rule (and the **Enforce Data Quality Constraint Rules** option is selected), the codes of the members will be included in logging.tSystemLog.

If the error limit is exceeded, the staging table's status is set to **Over the limit**. The staging table stops processing members and does not clear contents.

## SQL Errors

If the error returned is a SQL error (e.g. processing a Delete staging table) with members in use OR processing a merge staging table that violates a unique constraint (option configured in modeling), the entire transaction will be rolled back so both valid and invalid members included in the transaction are unchanged. The individual member codes are not included in logging.tSystemLog, but detail about the problem is included.

## Last Process Count

If a SQL error occurs while processing a member, that member is not added to the target table. However, that member is still counted under Last Process Count. If your table contains an Error status, note that not all processed members were processed successfully. SQL errors must be resolved before the table can finish processing.

To view and resolve the specific SQL error, [run a query](https://support.profisee.com/wikis/profiseeplatform/run_a_query) in SQL Server to return relevant messages.

## Gaps in Member Code

If the **Create code values automatically** option is selected, the Code value of an added member increases sequentially from the last added member. If an error prevents a member from being added, the Code for that member is counted and the next member's Code value may not be sequential. This can create gaps in the Code column between members.

For example; if members A, B, C, and D are added, but C fails, the staging table might read:

| | |
| --- | --- |
| **Member** | **Code** |
| A | 1 |
| B | 2 |
| D | 4 |

##