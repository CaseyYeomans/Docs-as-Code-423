# Review Changes in Published Models

Before you publish the system model to the server, Advanced Modeling first retrieves the model from the server and displays any differences between the source model and the target model in the Publish to Server dialog.

The source model is the version that exists in the modeling surface and contains your edits. The target model is the system model on the server. Any differences between the two are considered changes.

Possible changes include:

| Source object contains: | Target object in the same context contains: | Result |
| --- | --- | --- |
| GUID1 and Name1 | No object with GUID1 and no object with Name1 in the same context | The change displays as a **Create** at the object type level. Creates a new object in the specified context with Name1 and GUID1. |
| GUID1 and Name1 | GUID1 and Name1 | The change displays as an **Update** at the object type level. |
| GUID1 and Name2 | GUID1 and Name1 | The changes displays as an **Update** at the object type level. The target object is updated to match the settings of the source object with Name2. |
| No object with GUID1 and no object with Name1 in the same context | GUID1 and Name1 | The change displays as a **Delete** at the object type level. The object in the target is removed. |

The Publish to Server dialog also displays the Change Below icon for objects where a change to the model has occurred below the currently viewed level. Areas of the model that are identical in both the source and the target are marked with a check.

By default, the **Show Changes only** option is selected, and only differences between the source and target model display. To view all levels of the model, clear this option.

There are some scenarios not covered in the previous table that result in conflicts. A conflict occurs when a change in the source model does not cleanly map to the target model. When these issues occur, a conflict displays when you attempt to publish the model. The conflict is marked with a red flag icon. The valid options for resolving the conflict display, and you can select the most appropriate one. You must resolve any conflicts before you can publish the model. For more information, see [Conflicts and resolutions](https://support.profisee.com/wikis/profiseeplatform/conflicts_and_resolutions) and [Resolve conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_conflicts).