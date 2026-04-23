# Export and Import Subscriber Configurations

## Exporting Subscriber Configurations

To export one or more subscriber configurations:

1. In the navigation panel, under Administration, click **Subscriber configurations**.
2. Select one or more configurations in the list.
3. In the tab toolbar, click **Import/Export**.
4. On the menu, click **Export**.
5. Browse to the file location to save the configurations.
6. Click **OK**.

The subscriber configurations are saved in the selected location with the name and the file extension \*.subscriberconfig.

## Importing Subscriber Configurations

To import one or more subscriber configurations:

1. In the navigation panel, under Administration, click **Subscriber configurations**.
2. In the tab toolbar, click **Import/Export**.
3. On the menu, click **Import**.
4. Browse to the file location where the subscriber configurations are saved.
5. Select one or more subscriber configurations to import.
6. Click **Open**.

If multiple configurations were imported, they display in the list of subscriber configurations. If one was imported it opens in the edit panel.

To import subscriber configurations on a different server, first export the configuration from the source server. Connect to the target server with Profisee, and then import the configuration. Exported configuration files are saved on the client.

As of version 2020 R1, eventing subscriber libraries (DLLs) are stored in the file repository location specified during Configuration Manager setup of your instance under the folder **Profisee\Subscribers**. If upgrading from a prior release, you must copy any custom subscriber files to this new folder.