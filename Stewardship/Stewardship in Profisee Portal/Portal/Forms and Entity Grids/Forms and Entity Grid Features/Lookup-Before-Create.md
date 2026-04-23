# Lookup-Before-Create

The Lookup-Before-Create (LuBC) process helps prevent accidental duplication of data. When an entity grid has been configured for LuBC, it presents a preliminary data entry form to collect information from the user to allow the system to look for possible matches in the data before proceeding to the full configured add form. The search is supported by a configured matching strategy and the preliminary entry form includes all matching attributes configured for that strategy. A matching strategy is applied to search terms to find approximate matches and present them to the end user for review before a new record can be created.

## Performing LuBC

To perform a LuBC operation:

1. Enter values on the Preliminary Information form.
2. Click **Next**.
3. Matching data populates on the Possible Results page if the system is able to find existing records that match the preliminary data entered. If no matches were found, the add form is displayed, with relevant information from the Preliminary Information form populated in the appropriate fields.
4. Review the presented matches. The user can:
1. Open one of the existing records.
2. Click the **Proceed with add** button and continue to Step 5.
5. Complete the entry in the associated add form.
6. Click **Save** or **Save and Close** to save the new record to the server.

Data appears if the matching engine finds any existing records that match the preliminary data entered. LuBC results are displayed as a presentation view that is created by an administrator.

## Possible Matches

Follow-on actions depend on the search result.

### If Matching Results are Found

Select the desired record and right-click **Open Record**, or click the **Open Record tool icon** to review or change one of the possible matches. Opening an existing record completes the LuBC operation. You can also choose to add a record instead, even if possible matches were returned.

Once the form opened for the existing record is closed, the user is returned to the entity grid from which the LuBC was initiated.

### If No Matching Results are Found

The user is taken directly to the configured add form. The add form opens, pre-filled with the data entered on the Preliminary Information form where the form has these fields configured.

Clicking **C****ancel** returns the user to a blank entity grid, where the LuBC process can begin again.

## See Also

[Review Matching Results in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/review_matching_results_in_portal)

[Approve and Reject Match Group Records](https://support.profisee.com/wikis/profiseeplatform/approve_and_reject_match_group_members)