# Configure FastApp and Menu Icons

You can change the properties of the icons that appear in the sidebar on the Profisee web portal.

1. Navigate to **FastApps** in Profisee FastApp Studio.
2. Select the application you want to configure and click **Edit** to open the application view. Alternatively, double-click the application you want to configure to open the application view.
3. Do one of the following:

- **To edit an application icon**: Click the page header within the application view.
- **To edit a folder or page icon**: Navigate to the **Menu** tab, click **Edit**, then click the icon you want to configure.

4. Configure the menu using any of the following options.

- **Change Menu Name:**Under the **Name** field in the configuration window, input the name you want to display for that menu in the web portal.
- **Choose a Default Icon:** Clicking the Icon field launches the Icon selection dialog prepopulated with the Menu item name and a link to fontawesome.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4cc16436679264f9.png)Click the link to fontawesome.com and search the image library to find an icon to select. Example below searching for 'people' icons.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7ad7973287e1f743.png)Select an icon and copy the **Class name** by hovering over the html and selecting copy code snippet.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7c11c6af96977221.png)Paste the value into the **Icon name** field in FastApp Studio and click **save**. After clicking the save button, the icon name is automatically converted to the needed format

Profisee is licensed to use 'Pro' icons for menu items. As new versions of icons come out, we update our license to cover additional versions. See <https://support.profisee.com/wikis/profiseeplatform/credits> for versions of icons which are valid to use.

**NOTE**: Directly downloading an icon from fontawesome downloads the svg format which cannot be used for a FastApp icon (only png files are allowed here), and the Profisee 'Pro' license cannot be used to download these files.

- **Upload Additional Icon:** Click the **+** icon to upload a .png image from your machine to act as the icon for this menu item. The image can be no larger than 500x500 pixels.
- **Delete the Selected Image:**Click the Binicon to delete the currently selected menu icon.

5. Click **Save** in the configuration window.
6. Click **Save** within the application context if editing a folder or page icon.