# DeleteRecord

The **Deleterecord** activity deletes a specified record record from an Entity based on the **EntityId** specified in the **RecordDataContext** argument and the **Code** value.

| | | |
| --- | --- | --- |
| **Deleterecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | The**RecordDataContext** object. |
| Code | String | The **Code** of the record to delete. |
| **Deleterecord Out Arguments** | | |
| Errors | Collection<Error> | A collection of errors returned from the **DeleteRecord** request. |

*\*Argument is required*

### Remarks

The DeleteRecord activity accepts a RecordDataContext object and a record code string. If a Code argument is not supplied, the system will use the RecordId specified in the RecordDataContext object. This activity returns a collection of Errors if any occurred while trying to delete the record.

### See Also

- [Delete records](https://support.profisee.com/wikis/profiseeplatform/delete_members)