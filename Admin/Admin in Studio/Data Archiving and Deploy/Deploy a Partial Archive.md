# Deploy a Partial Archive

Instead of deploying all the data in an archive, you can deploy a portion of it by skipping model objects.

To deploy a partial archive by skipping objects:

1. In the Data Deployment tab, open an archive file.
2. Right-click an object in the tree.
3. Click **Skip** on the menu.

The object is marked with a white flag icon and the text **Skip** appears to the right of the object name.
4. Skip other objects as necessary.
5. Resolve any conflicts as explained in [Resolve Data Archive Mapping Conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_data_archive_mapping_conflicts).
6. Click **Deploy To Server**.

The archive deploys to the system model, omitting any data from skipped objects.

You can only skip the Code attribute when you also skip the entire related entity.

Skipping an object can cause other objects to be skipped (dependent skips). For example, if you skip an entity that is linked to a domain-based attribute, then you cannot include consolidated member data for that entity.