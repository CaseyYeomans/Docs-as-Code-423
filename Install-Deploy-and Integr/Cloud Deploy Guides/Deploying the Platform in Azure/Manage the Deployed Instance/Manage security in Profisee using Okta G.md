# Managing security in Profisee using Okta Groups

### Groups Claims Setup for Okta

There are two places to set up groups claims: **server** level and **app** level. The app level claim is the one we need to configure.
Filtering in general: Please create an easy to follow naming convention and use it to your advantage: ex App\_Environment\_Role:
Profisee\_Dev\_DataStewards
Profisee\_Dev\_Admins
Profisee\_Test\_DataStewards
Profisee\_Test\_Admins
Profisee\_Prod\_DataStewards
Profisee\_Prod\_Admins
OtherApp\_Dev\_SomeRole
OtherApp\_Test\_SomeRole, etc.
Filter on "Profisee\_Dev", "Profisee\_Test", etc. In the examples below, the number serves to indicate how many groups to return, between 1 and 100.

### Server Level Setup

1. Log into **Okta**, then go to **Security** > **API**, then select your auth server that handles the Profisee applications. If you have more than one, click on the one that contains your Profisee applications.
2. Click on the **Scopes** tab.
3. Add a scope for groups by clicking on **Add Scope**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9517c334d0c16df0.png)
4. Consult with your security engineers on what to select for the User Consent. The name of the scope must be "groups". Suggested for **Display phrase** and **Description** are the following: "View your group memberships" and "The exact groups vary based on what filtering is used in the application." Since filtering is involved on the app level, only the groups that are relevant to the specific environment will be present in the claims received by Profisee.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id3522b72a3179137.png)

### App Level Setup

1. Go to **Okta** > **Applications** > **Applications**, then select the specific app for the respective environment (Dev in our example), then **Sign On** tab, then **OpenID Connect ID Token** section, **Edit** and then use either: a simple filter like the following.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i18ca5609b4cc932a.png)**OR** use an expression to specify "OKTA" for Okta sourced groups, such as the following.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i410f42250de143df.png)
**OR** use an **expression** to specify "active\_directory," if those groups are sourced from AD.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6beed2dfd9472f28.png)
2. Click the Assignments tab, click the **Assign** button, select **Assign to Groups**, then click **Assign** beside each group that should belong to that environment; ideally anything that starts with Profisee\_Dev, if you've followed the example above for your Dev environment. Please do not add users here. If there are users, either remove them (so they get added through the group you are assigning to this application) or convert those user assignments to groups.

Note that in our tests, the **getFilteredGroups** expression filter did not work. Our authentication service expects a claim for each group. We believe the getFilteredGroups returns a multi-string value, which fails to be interpreted.

Once this setup is done, please have the SuperAdmin in the respective Profisee environment log in to Fast App Studio, go to **Administration**, then **Accounts and Teams**, then **Accounts**, then **New**. Make sure to add the full group name under **Group Accounts** (lower box) as configured in Okta, then click OK. Double click the newly added group (or select it and click **Edit**), click **Roles** and assign a Profisee role to the group. Click **Save & Close** to finish the setup for this group. Repeat for any other groups.

Note: You can add multiple groups in the User or Groups window, comma-separated.