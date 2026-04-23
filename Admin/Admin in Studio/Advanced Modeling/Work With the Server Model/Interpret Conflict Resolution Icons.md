# Interpret Conflict Resolution Icons

When you attempt to publish it a model after making changes, the local model that you have edited (the source model) is compared with the model on the server (the target model).

The following icons provide visual cues that help you understand the changes to the model:

| Icon | Meaning |
| --- | --- |
| | The source and target versions of this object are identical. |
| | An object below the current level has changed. |
| | This object is different in the source model. |
| | This is a new object in the source that will be created on the target. |
| | This object has been deleted and will be removed from the target. |
| | This attribute has the same name as an attribute on the server, but has a different data type. The attribute on the server will be deleted and replaced with this attribute. |
| | There is a conflict and the object on the server will not be updated unless the conflict is resolved. Right-click for conflict resolution options. |
| | Because the user has selected to skip this object, this object will not be updated in the target model although the source and target differ. |

For more information, see [Resolve conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_conflicts) and [Conflicts and resolutions](https://support.profisee.com/wikis/profiseeplatform/conflicts_and_resolutions).