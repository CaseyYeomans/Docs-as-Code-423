# RecordDataContext Type

The **RecordDataContext** type provides all of the identifying attributes of a record to allow it to be both presented to users and read from the server in various workflow activities.

**Namespace**: Profisee.MasterDataMaestro.Services.Contracts.DataContracts.Portal

### Properties

|  |  |  |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| RecordId | [RecordIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) | Uniquely identifies a record record. |
| TransactionId | Nullable<long> | Identifies the ID of the transaction that with which the **RecordDataContext** is associated. This value is set only when the **RecordDataContext** is passed as an argument to a workflow from the real-time event processing subsystem. This allows the workflow to have access to the transaction that caused the workflow to be started. |
| EntityId | [ModelContextIdentifier](https://support.profisee.com/wikis/profiseeplatform/modelcontextidentifier_type) | Identifies the Entity and the associated Model with which the **RecordId** value is associated. |

### Remarks

The **RecordDataContext** type is used extensively throughout workflow activities to identify the record record that is being processed by the workflow and its associated activities. In addition to the key to the record, the context includes the **EntityId** which also includes the entity’s associated Model.

> [!NOTE]
> With release 7 of the platform, the Profisee moved to a single model per instance approach. Therefore, the Model identifier is a static value and can be ignored. It is maintained merely for backward compatibility support.

When Profisee’s real-time event management subsystem triggers a workflow to be started, it passes a **RecordDataContext** object to the workflow so the workflow knows on which record record to operate. When passed by the real-time event management subsystem, the **TransactionId** is set to the transaction that caused the event to be triggered. In doing so, the workflow then has access to the transaction to allow it to be reversed based on task activities associated with the workflow.

Profisee workflow activities exist to allow a workflow designer to create new instances of the **RecordDataContext** type during workflow processing. Refer to the [NewRecordDataContext](https://support.profisee.com/wikis/profiseeplatform/new_member_data_context_activity) and [CreateRecordDataContext](https://support.profisee.com/wikis/profiseeplatform/create_member_data_context) activities for details.

---

### See Also

* ​​[Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
* [ModelContextIdentifier](https://support.profisee.com/wikis/profiseeplatform/modelcontextidentifier_type)
* [RecordIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)