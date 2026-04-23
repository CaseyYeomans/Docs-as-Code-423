# CreateRecordDataContext

Given an entity name and record code, the CreateRecordDataContext activity returns a new RecordDataContext object.

| | | |
| --- | --- | --- |
| **CreateRecordDataContext****In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Entity\* | String | The entity name string |
| Code | String | The record code string |

| | | |
| --- | --- | --- |
| **CreateRecordDataContext Out Arguments** | | |
| RecordDataContext | RecordDataContext | The RecordDataContext object. |

*\*Argument is required*

### Remarks

The CreateRecordDataContext activity accepts an entity name string and a record code string as an in arguments. The entity argument is required. The activity returns a new RecordDataContext object for the entity (and optionally code) that can be used in the following workflow activity.

Note that the CreateRecordDataContext and NewRecordDataContext activities are identical, except that the CreateRecordDataContext requires the entity name during workflow design/development time, while the NewRecordDataContext allows workflow administrators to dynamically set the entity after the workflow is registered in FastApp Studio in the workflow configuration.

### See Also

[New Record Data Context](https://support.profisee.com/wikis/profiseeplatform/new_member_data_context_activity)