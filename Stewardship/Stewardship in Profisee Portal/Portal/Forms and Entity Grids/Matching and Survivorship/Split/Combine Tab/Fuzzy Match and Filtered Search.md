# Fuzzy Match and Filtered Search

From the Match Stewardship window in the Profisee FastApps portal, you can use the Fuzzy Match and Filtered Search functions to find specific members for match stewardship. Once you search or filter on specific parameters, the Match Group field populates with members that match those parameters. Once listed, you can [move these members to new match groups](https://support.profisee.com/wikis/profiseeplatform/move_members_to_alternate_group).

1. Navigate to the Match Stewardship page within the Profisee FastApp portal.
2. Click the **Group/Membership** toggle in the top-right corner of the Match Stewardship window to navigate to Split/Combine view.
3. Select either the **Fuzzy Match** or **Filtered Search** button on the top-right of the Match Stewardship tab. Alternatively, right-click a listed member and select **Fuzzy Match** or **Filtered Search** from the dropdown menu.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib0e6d6d4c24231a4.png)

## Fuzzy Match

Fuzzy Match allows you to search on specified attributes to return similar members. This function uses the existing matching strategy logic to search for members. You may only change the value to search. Only members that are in the matching index are returned in this search. Members may be excluded from the matching index based on matching strategy criteria OR because indexing has not run since the member was added or values were updated.

To perform a fuzzy match search, specify the desired values for the attributes on which you want to search (either through free-form text entry or by a dropdown menu), then click **Submit**. If you want to clear all entered values, click the **Clear** button on the top left corner of the window.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic371f6d514d4560d.png)

## Filtered Search

Filtered Search allows you to find members by specifying assertions about relevant members. This function defaults to the attributes in the matching strategy, but the attributes operators and values can be changed. The matching index is not involved, so members are not excluded based on matching criteria or index state.

When you perform a filtered search, one filter row appears by default. To add a new row, click the green **Add** button in the top left-corner of the window. If you want to delete a row, click the red **Delete** button in the top-left corner of the window. You can reorder the attribute rows by selecting one or more rows and clicking **Move Up** or **Move Down** on the toolbar. You can also group and ungroup rows using the **Group** and **Ungroup** buttons on the toolbar. If you want to clear all attributes from the filter table, select **Delete all rows**.

Once your table is configured as desired, you can specify the values on which you want to perform your filtered search.

1. Select the **Attribute** on which the search is filtered.
2. Select the filter **Operator** to define the context in which the value is filtered.
3. Select the **Value** the operator defines.
4. Ifentering additional rows, designate them as **And** or **Or**. If a row is designated as And, the filtered results adhere to both search criteria. If a row is designated as Or, the filtered results adhere to either search criteria.
5. Click **Save**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5e275887a8e575e2.png)