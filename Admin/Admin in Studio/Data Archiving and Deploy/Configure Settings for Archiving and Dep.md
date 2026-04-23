# Configure Settings for Archiving and Deployment

Several settings affect data archiving and deployment performance. Begin with the default settings, and then change them later to fine-tune performance. Refer to [Best practices for data archiving and deployment](https://support.profisee.com/wikis/profiseeplatform/best_practices_for_data_archiving_and_deployment) for additional tips on using Data Archiving and Deployment.

## Data Archiving Settings

Under FastApps Studio Settings:

- **Data Archiving tab**: Maximum number of cores

Controls the number of client cores used during the archiving process
- **Entity tab**: Batch size (default = 1000)

Controls the number of members included in each batch during archiving

## Data Deployment Settings

Under FastApps Studio Settings:

- **Entity tab**: Publish batch size (default = 50)

Controls the number of members included in each batch during deployment

The Command Line Utility does not use these settings but instead uses specific archiving and deployment command line options. For more information, see [Data Archiving and Deployment CLU reference](https://support.profisee.com/wikis/profiseeplatform/command_line_utlity_reference_for_data_archiving_and_deployment).