# DeleteRecords

The **DeleteRecords** activity deletes a specified record record from an Entity based on the **EntityId** specified in the **RecordDataContext** argument and the **Code** value.

| | | |
| --- | --- | --- |
| **DeleteRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | The**RecordDataContext** object. |
| RecordCodes\* | Collection<string> | The **Codes** of the records to delete. |
| **DeleteRecord Out Arguments** | | |
| Errors | Collection<Error> | A collection of errors returned from the **DeleteRecord** request. |

*\*Argument is required*

### Remarks

The DeleteRecords activity requires a RecordDataContext object and a collection of record code strings. This activity returns a collection of Errors if any occurred while trying to delete the records.

### See Also

- [Delete Record](https://support.profisee.com/wikis/profiseeplatform/delete_member)