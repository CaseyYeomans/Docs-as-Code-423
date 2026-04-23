# Deploy an Archive

After you have created and processed an archiving strategy, you can deploy the compressed archive.

To deploy an archive:

1. In the navigation panel, under Administration, click **Data Archiving and Deployment**.
2. On the Data Archiving and Deployment tab, click **Deploy data**.
3. On the deployment toolbar, click **Open Archive**.

If the tab is not already open, then the Open Archive File dialog opens automatically.

4. Browse to the archive file.
5. Select the file, and then click **Open**.

Data Deployment compares the metadata in the archive to the metadata in the system model. If there are differences, conflicts display in the model tree.
6. Review the information in the **Source and content** section of the Data Deployment tab.

The following information displays about the selected archive:

- Server
- Version
- Filter
- Created On
- Created By
- Entity count
- Member count
7. Resolve any conflicts in the Deployment Targets tree.

For more information, see [Resolve Data Archive Mapping Conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_data_archive_mapping_conflicts).

If extensive remapping is required before you can deploy the archive, edit the system model first using Advanced Modeling, and then return to Data Deployment to deploy the archive. Data Deployment includes basic tools for resolving mapping issues, but it is not a replacement for Advanced Modeling.

8. In the Data Deployment toolbar, click **Deploy To Server**.

The Data Deployment Status dialog appears, and the model data immediately begins deploying to the target.
9. When the Summary line displays in bold, deployment is complete. You can then close the Data Deployment Status dialog.

Deployment takes much longer than archiving. The speed of deployment depends upon many factors, foremost your hardware and the number of records you are deploying. Deploying tens of millions of records could potentially take several days to complete.

When an archive is deployed, the `*.bin` files containing model object information are extracted to the local computer before the data is deployed to the server. For this reason, it is important to have sufficient hard drive space available locally before deploying a large archive.