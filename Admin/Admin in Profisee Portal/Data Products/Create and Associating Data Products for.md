# Creating and Associating Data Products for Purview

Profisee admins with an [integrated Purview instance](https://support.profisee.com/wikis/profiseeplatform/azure_preview_overview) can associate data products between both platforms. This association causes Profisee entities to appear natively inside the Purview Data Catalog, and ensures changes made to Profisee data assets (such as attributes, relationships, hierarchies, etc.) are persisted across both platforms.

This feature requires **Super Administrator** privileges in Profisee and the **Data Product Owne**r role in Purview.

## Creating/Configuring a Purview Data Product for Profisee

Before a Profisee Data Product can be linked to Purview, you must first create a Purview Data Product. Purview Data Products can be accessed from the Purview home page > Unified Catalog > Catalog Management > Data Products. Here you can access a list of all previously created data products, or create a new Purview data product by clicking **New data product.**
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id7995d748ef449cc.png)

For any additional information on Purview beyond what is provided below, consult the [Purview Documentation](https://learn.microsoft.com/en-us/purview/concept-data-products) on the Microsoft wiki.

### Create a New Data Product

1. Add a name and a description for your data product.
2. Select the **Master data and reference data** Type from the dropdown list. Selecting any other type will prevent compatibility between the platforms.
3. Select an Owner for this data product.
4. Click **Next**.
5. Select a Governance domain to be associated with this data product.
6. Input a use case for the Data Product in plain text.
7. Choose whether to mark the data product as Endorsed. This option does not affect compatibility with Profisee.
8. Click **Create**.

### Configure a Purview Data Product to be Compatible with Profisee

Purview Data Products must meet certain criteria before they can be visible to Profisee. To ensure your Purview Data Product is compatible with Profisee:

1. Navigate to your desired Data Product in Purview.
2. Click Add under **Glossary terms**and select the Profisee MDM glossary term under all relevant domains. If this glossary term does not already exist, it must be added by a Purview administrator.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2e20f4e32395e18b.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7bc4e9c8ec02c7ac.png)
3. Click **Add**.

## Associating Data Products

Once you have at least one existing Purview Data Product that has been configured for use in Profisee, you can associate a new Profisee Data Product with that Purview Data Product. To do so:

1. Navigate to the Administration area of Profisee Portal and [create or edit a new data product](https://support.profisee.com/wikis/profiseeplatform/create_edit_delete_data_products). If your instance is integrated with Purview, the *Create Data Product* window will contain the header *Associated Purview Product*.
2. Select a Purview Data Product from the dropdown list.
3. Click the move arrow on the entities in the *Available Entities* list to add them to the *Associated Entities* list for Purview. You can also click the move arrow on an entity from the *Associated Entities* list to remove it from the association.
4. Click Create to create the data product and the association.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5a87cde930f2ba6f.png)

Once one or more data products have been associated with Purview, those data products will also appear in the Governance Details for those related entities. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i707632a626bfd300.png)

##