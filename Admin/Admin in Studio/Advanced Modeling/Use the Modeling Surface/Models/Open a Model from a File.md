# Open a Model from a File

Open one or more model files in the modeling surface at the same time. Open the system model and multiple models from files simultaneously to copy objects from one model to another.

### Open the system model in Advanced Modeling:

1. Click **Open** on the modeling toolbar.
2. Click **Open from Server** on the menu.

The application retrieves the system model and opens the tree view pane of the Advanced Modeling tab. The file name displays as the name of the model.
3. Choose whether to check out the model in the **Check out the model from the server** dialog, if applicable. The option does not appear if the user already has the model checked out.

### Open a model in Advanced Modeling from a local file:

1. Click **Open** on the modeling toolbar.
2. Select **Open File** on the menu.
3. Navigate to the location where the model file is stored and select it.
4. Click **Open**.

The model opens in the tree view pane of the Advanced Modeling tab. The file name displays as the name of the model.

You must have the System Administrator role to open the system model.

Model files are XML files and have the extension .maestromodel. When you check out the system model, it remains checked out until it is checked in again. The checkout will block other application features from making changes to the model. You can view the model and make changes, but you cannot publish the model without checking it out first.