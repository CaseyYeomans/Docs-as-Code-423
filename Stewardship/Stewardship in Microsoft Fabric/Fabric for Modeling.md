# Using Fabric for Modeling

Once your Profisee and Data Fabric environments are connected, you can perform basic data modeling and stewardship tasks such as creating, editing, and deleting Data Products and Entities, and managing the data contained within them. Changes made to entities in Fabric are persisted into the Profisee instance.

From your previously created data product in Fabric, entities associated with that data product are populated in a stewardship view that allows you to add, edit, and delete records.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibaec6315dff1af01.png)

## Add New Entities to a Data Product

To add new entities to a data product:

1. Click the horizontal ellipsis icon next to your Data Product name within the Explorer.
2. Select **Create New Entity.**![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibd32d078a45e0afb.png)
3. Enter a name for the new entity.
4. Click **Create**.
5. An empty entity is created, and an empty entity grid is opened.

## Connect a Data Product to an Existing Entity

To connect your Data Product to an existing entity:

1. Click the horizontal ellipsis icon next to your Data Product name within the Explorer.
2. Select **Connect to Existing Entity**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibd32d078a45e0afb.png)
3. Select an entity from the dropdown list. This list of entities is populated based on your connected Profisee instance.
4. Click **Connect**.
5. The entity is added to your Data Product, and the entity opens as an entity grid on the page.

## Add or Edit Attributes to an Entity

Once your Data Product is associated with at least one entity, you can create or edit attributes within that entity. You can consider an Attribute as a data category, such as Size or Price, that allows you to define specific information within a record. You must create at least one attribute for your entity before you can populate your entity with new records.

1. Click the vertical ellipsis icon on the toolbar and select **Edit Attribute** or **Create Attribute**.
2. Input or edit the desired values for the attribute, then click Save.

See [here](http://support.profisee.com/wikis/profiseeplatform/create_and_edit_attributes_in_the_portal) for more information on creating or editing attributes.

## Create New Records

Once your Data Product has at least one entity with at least one attribute, you can begin populating your entity with Records, which are specific objects by which data is assigned and managed. A Record might take the form of an individual product or a customer. To create a new record:

1. Click the **+** icon on the top toolbar. The New Record pane opens.
2. Enter a **Name**, **Code**, and **Description** for your record.
3. Click **Save** or **Save and Close**.