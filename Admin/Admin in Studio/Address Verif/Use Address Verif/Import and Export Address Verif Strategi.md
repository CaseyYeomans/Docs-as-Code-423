# Import and Export Address Verification Strategies

Importing and exporting provide a method of moving address verification strategies between environments. It is possible to use the same strategy from a development environment in a production environment by saving a file and then opening it on a different server. Exporting strategies is also a useful method for backing up verification strategies and for troubleshooting.

Adjustments are generally required after strategies are imported. Because metadata IDs are different in different environments, and because output attributes may not yet exist, it is usually impossible to import and immediately use an address verification strategy. Any strategies with inconsistencies are flagged with a red exclamation mark to help you locate issues and update the strategy so it functions in the new environment.

To import a strategy:

1. In the navigation panel, click **Administration**.
2. Click **Address Verification**.
3. On the Address Verification toolbar, click **Import/Export** to open the menu, and then click **Import**.
4. Locate the saved strategy file location.
5. Select one or more strategies to import, and then click **Open**.

To export strategies:

1. In the navigation panel, click **Administration**.
2. Click **Address Verification**.
3. Select one or more address verification strategies to export.
4. On the Address Verification toolbar, click **Import/Export** to open the menu, and then click **Export**.
5. Do one of the following:

**--or--**

- For a single strategy: Choose a file location, include a name for the file, and then click **Save**.
- For multiple strategies: Choose a file location and then click **OK**.

The files are saved with default names based on the strategy name and the time and date they were exported.

Strategies saved prior to licensing changes must be opened and re-saved after they are imported.

For information on importing older address verification strategies, see [Importing location verification strategies created prior to Profisee version 4.0.3.](https://support.profisee.com/wikis/profiseeplatform/update_location_verification_strategies_created_prior_to_maestro_4_0_3)