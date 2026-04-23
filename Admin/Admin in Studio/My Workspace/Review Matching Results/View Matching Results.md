# View Matching Results

The Matching Results view lets you review and work with matching results.

From this view, you can:

- Review and approve or reject matches
- Look for alternative matches
- View promoted and harmonized values
- Manually promote or harmonize values
- View the details of matching calculations
- Find alternative matches for matched records
- Incrementally match new, unmatched records
- Sort and filter your matching results

The Matching Results view provides grid panels with a sortable and filterable record grid at the top and a match group grid at the bottom.

## Access Matching Results

To open the view:

1. From My Workspace in the navigation pane, click **New**, and then select the **Matching Results** view tab.

**--or--**

From the Strategy menu, select the strategy with the results you want to view. You can clear **Start with a Results Summary view** to skip the summary and go directly to Matching Results.
2. Click **OK**.
3. Click either **Refresh Results** or **Show Prior Results**. The Matching Results tab opens.

Refreshing the strategy matching results may take a long time, depending on data volume. Showing prior results may be quicker, but the information displayed may be less accurate, depending on whether users or processes have made incremental changes since the last batch matching run.

## Match Record Grid (First Grid)

This is the main grid in the Matching Results tab and lists the records from the entity referenced by the matching strategy. This entity contains the source records and the optional golden records created during the matching process. The way the records display in the top grid is controlled by the current View menu selection.

The columns (attributes) displayed are relevant to the matching strategy and the selected view. You can add additional columns to the display by clicking **Columns** in the toolbar. From this grid, you can search and filter records as you work through the matching results review and approval process. Selecting a record in this top grid lets you see the related match group in the bottom grid.

## Selected Group Grid (Second Grid)

The selected group grid displays the match group for the selected record in the top grid. If golden records were created, the golden record record is displayed and highlighted as the first record in the list. The Match Status and Match Score indicate which groups require additional review, such as when groups contain proposed records. The main purpose of this grid is to review match groups and work with match group record data.

## Pinned Group Grid (Third Grid)

If you pin a selected match group, it moves to the bottom of the Matching Results tab. The pinned group continues to display when you select other records in the top grid. The pinned group grid allows two match groups to display at the same time so that you can move records between them.

## Sort and Filter the Grids

You can use the same tools to sort and filter your matching results that you use for the entity grid. For more information, see [Build an entity grid filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter) and [Sort the entity grid](https://support.profisee.com/wikis/profiseeplatform/sort_the_entity_grid).

## Predefined Views

Choose predefined matching results views by selecting one of the View menu options:

- **Approved Matches**

Source records that are approved matches. Includes records with match statuses of AutoApproved, Approved, and UserMapped.
- **Proposed Matches**

Source records that are similar enough to match above the Match Threshold but require user review to confirm the match. Includes records with a match status of Proposed only.
- **Unique Records**

Unique records (records with a match status of Unique)
- **Unmatched Records and Excluded Records**

Source records unprocessed by matching. These could be new records, records excluded from matching by strategy criteria, or records with matching attributes that contained blank values. These are records with no match status.
- **Rejected Records**

Match group records that were rejected during matching results review (records with a match status of Rejected)
- **Match Groups with Proposed or Rejected**

golden records with one or more proposed matches (records with a match status of Golden Record and a proposed count greater than 0)
- **Match Groups with only Approved**

Golden Records with one or more approved matches (records with a match status of Golden Record and an approved count greater than 0)
- **Golden Records**

Records with a match status of Golden Record
- **Match Groups**

All match group records sorted by Group ID

Approved records include both matches that were auto-approved during the matching process and manual user-approved and user-mapped matches. If you have not created golden records with survivorship and select one of the golden record views, no records display in the first grid.

You can add additional attributes columns to any view. For more information, see [Viewing additional attribute columns](https://support.profisee.com/wikis/profiseeplatform/view_additional_attribute_columns).

If the survivorship portion of the strategy does not have Update counts on golden records after survivorship selected, the Approved and Proposed Counts will be blank.