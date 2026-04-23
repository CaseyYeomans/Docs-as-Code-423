# Best Practices for Model Management when Deploying Applications

Most organizations implement multiple environments when implementing software applications. A common setup uses three environments: development, test, and production. The deployment of models between these three environments must be carefully managed and, where possible, automated to prevent user error.

Deploying your solution to a new environment involves first exporting the model to a file along with related solution artifacts such as strategies, rules, forms, applications, etc. The next step is to import the model and the strategies, lists, rules and views.

## The Importance of GUIDs

Care must be taken when deploying models to different environments because model metadata contains GUIDs. GUID references are necessary to correctly map strategies and other exported items associated with models. Whenever a new model is created, new GUIDs are created for the model metadata. When the GUIDs for the source and target model do not match, importing exported items becomes much more difficult. For this reason, it is important to use the same model metadata when moving a model between environments.

## Change Control and Profisee

A general Profisee deployment process includes these steps:

1. Create portable definition files in XML format for metadata and model items (such as rules, lists, views and strategies)
2. Export the data using data archiving
3. Check the files into a source control environment such as TFS
4. Check out the files from source control when ready to deploy them
5. Deploy the files to the target environment
6. Deploy the data using data deployment

See [Process an Archiving Strategy](https://support.profisee.com/wikis/profiseeplatform/process_an_archiving_strategy) for the specific steps involved in deploying data to a model.

Keep in mind that security, permissions, and Profisee System Settings are not replicated in the deployed model. These settings must be re-created manually.

## Maintaining GUID Integrity

Certain metadata creation methods produce models and model objects that are similar to the source model without maintaining the same GUIDs. To ensure your model strategies, rules, views, and lists import without issue, avoid creating a model object (such as an attribute) or any application elements directly (manually, through an Attribute Assistant, through data import) in a production environment after creating them in a test or development environment. The name and context may be the same, but they are not identical because the GUIDs are different.