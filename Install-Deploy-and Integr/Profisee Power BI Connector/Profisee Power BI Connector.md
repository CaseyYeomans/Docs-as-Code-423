# Using the Profisee Power BI Connector

To use the Profisee Power BI connector:

1. Open Power BI Desktop.
2. Navigate to **Options > Security**.
3. Check the **Use my default web browser** option under **Authentication Browser**, then click **OK**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i966d5e2ec40dd801.jpeg)
4. Click the **Get Data** option in the **Home** ribbon to open the **Get Data** dialogue.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if0bcef13fc77edbc.png)
5. Enter Profisee into the Search box or select **Online Services** and select Profisee from the list, then click **Connect**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5d22793fe4e15f07.png)
6. Click **Continue** on the following dialogue. Optionally, select the checkbox to prevent this dialogue from appearing in the future. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i73eb116b1ce7ad15.png)
7. Enter the URL for your Profisee instance, then click **OK**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3a7b147312aa2f9a.png)

If it is your first time connecting, you will be prompted to log in using an authentication service. For additional information on signing on with authentication, refer to the Help article on [Authentication](https://support.profisee.com/wikis/profiseeplatform/log_in_to_the_profisee_platform).![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ife4042aa9f37f5fa.png)

8. Click **Connect**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5af2d24b088cf2c0.png)
Once connected, the Navigator is displayed. This display lists all entities in your Profisee instance. You can scroll through the navigator to locate specific entities, or search for entities by name using the search bar.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iafda423bd5f2e18d.png)
9. Select the entities that you want to import into Power BI. You can preview the data and choose to either first **Transform Data** if you want to edit the attribute columns, apply filters, etc. or **Load** the data directly into Power BI Desktop.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie17547943e33476d.png)
10. Once Loaded, the entities appear in the model view, and you can view the attributes ready for use in Power BI in the **Fields** dialog.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3521196d35f2b077.png)

Note that relationships in Profisee are not created in the model in Power BI. After the entities are loaded, you can view the Model and create or modify relationships as desired.