# Configuring the Lookup Tab

Lookup-Before-Create (LuBC) allows you to configure the behavior and appearance of LuBC if it is enabled on a portal page's entity grid control. To do so, create a presentation view to display the desired attributes that are returned for LuBC. It is recommended to use Name, Code (if meaningful), attributes used for matching, and any additional attributes that might aid in determining if the record is a match to the record being created. Additionally, when viewed in the portal, a **Similarity**column is added to as the first column in this presentation view automatically. Results are displayed in descending order of similarity.

1. Selectwhether to include all records, golden records only, or source records only.
2. Select an entity to be used for the Results View.
3. Select the presentation view you want to use to display LuBC results under the **Results view** dropdown list.
4. Select the order of the attributes to be displayed during LuBC results.
5. Enter a column label for each attribute to be displayed during LuBC results.

If no presentation view is selected, the LuBC results will be displayed with the columns: **Code**,**Name**,**[Matching Attributes]**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i76cd97a6c7726f46.png)

---