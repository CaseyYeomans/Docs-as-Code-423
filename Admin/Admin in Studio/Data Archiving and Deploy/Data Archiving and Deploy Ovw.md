# Data Archiving and Deployment Overview

Data archiving and deployment makes it possible for model administrators to archive and deploy model data within the FastApps Studio interface.

Options are available to archive the entire model or a selected group of objects within the model. Any dependent objects required to populate other objects, such as domain entities for DBAs, are included automatically in the archive. You cannot create a strategy which omits a dependent object from the resulting archive.

Archiving and deployment involves three steps:

1. Creating an archiving strategy
2. Processing the strategy to create an archive file
3. Deploying the archive file

Because the archiving portion of the tool uses a server-based strategy, you can archive the same data over and over again. This makes the tool ideal for backup purposes, as you can ensure that the data for the same model areas is archived each time. Incremental strategies are easy to create and modify using the strategy **Filter by Last Updated On** filter. Archive files can be stored as backups, or deployed to other servers.

The model can change over time as attributes can be renamed, entities can be deleted, and other metadata changes can occur. Deployment never deletes data. Instead, it merges deployed data with existing data on the server, such as added members or edited entries for existing members.

During the archive deployment phase, the conflict resolution process alerts you about any inconsistencies between the archive and the target metadata. Tools are available within the interface to resolve any conflicts in the best way for your purposes. Deployment also allows flexibility, including options for deploying an entire archive, or just a portion of it.

You can export archiving strategies and import them to other servers, allowing strategy reuse in other environments. Any metadata inconsistencies in the strategy are flagged to show where mapping corrections are needed. After missing model elements are remapped, you can then save and use the imported strategy to create archives for the new environment.

## See Also

[Create an Archiving Strategy](https://support.profisee.com/wikis/profiseeplatform/create_an_archiving_strategy)

[Process an Archiving Strategy](https://support.profisee.com/wikis/profiseeplatform/process_an_archiving_strategy)

[Deploy an Archive](https://support.profisee.com/wikis/profiseeplatform/deploy_an_archive)