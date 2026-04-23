# Resolve Data Archive Mapping Conflicts

Controls referenced in this instruction:

| | |
| --- | --- |
| | Mapping Issues Below |
| | Red Flag |
| | White Flag |
| | Green Check |
| | Add Member |
| | Deploy to Server |

The indicator **Mapping Issues Below** can display when an archive is opened in Data Deployment. It indicates that a mapping conflict exists between the archive and the target model. This situation can occur when the metadata of the source model for the archive has changed since the archive was created.

Mapping issues can occur for the following reasons:

- A model object exists in the archive that does not exist in the system model
- An attribute in the system model has properties (data type, length, number of decimals) that are incompatible with the corresponding source attribute in the archive, and data for that attribute cannot be deployed with the current mapping
- Resolving another conflict has caused a mapping issue

Mapping issues indicate that there is no clear target to restore archived data to. You cannot deploy an archive until all archive conflicts are resolved.

You can resolve a conflict in three ways:

- Map the archived object to a different object in the system model
- Skip the object that is in conflict

The Code attribute is an exception. It cannot be skipped.

- Create a new object in the system model

To resolve a data deployment mapping conflict:

1. Expand the top level of the model.
2. Continue to expand levels marked with the **Mapping Issues Below** indicator.

The down arrow indicator means that one or more issues exist at a deeper level in the model.

3. When you find an object marked with a red flag icon, you have located the conflict.
4. Right-click the object marked with the red flag icon.
5. Click one of the menu options:

If you attempt to remap an object and you get the message that all possible targets are mapped, you can either skip the object or create a new object. Alternatively, you can exit Archiving and Deployment and open the model in Advanced Modeling to use additional model editing options. Sometimes, more complex issues exist in the target model than can be resolved using the conflict resolution options.

- **Skip**: Skip the archived data and metadata for this object

The red flag icon changes to a white flag icon. The text to the right of the skip indicates that this object is skipped. The data associated with the object will not be deployed.

**NOTE**: To undo a skip, right-click the object again, and then click **Include**.
- **Map To Target**: Map the archived object to a different object in the system model

Objects must be mapped to the same object type. Remapped attributes must also have the same data type and compatible properties, including length and number of decimals.

1. From the Target list in the Map To Target dialog, select the model object to map to.
2. Click **OK**.

In the model tree, the red flag icon is replaced with a green check.

- **Create New**: Create a new model object to the specifications required by the object in the model archive

1. In the **Create New** dialog, type a name for the object.
2. Click **OK**.

In the model tree, the red flag icon is replaced with a plus sign.

6. When all the conflicts are resolved, click **Deploy To Server** to deploy the data.

The data deploys according to your selections.