# Match New Unmatched Members Incrementally

When new members are added to an entity, you can match them against current match results without reprocessing the entire strategy. Before you can match from the Matching Results tab, the strategy must be batch processed at least once (from the Matching and Survivorship tab of the Administration area). The index for the matching strategy must also be loaded in memory.

To perform incremental matching:

1. Open a Matching Results view tab.
2. From the Strategy menu, select the strategy with the results you want to view.
3. Clear **Start with a Results Summary view** to skip the summary and go directly to Matching Results, and then click **OK**.

The Matching Results tab opens.
4. From the View menu, select **Unmatched and Excluded Members**.

The members with no match status display. This view also includes members filtered by any criteria in the matching strategy.
5. Right-click the member you want to match, and then click **View Possible Matches** on the menu.

The Matches dialog appears.
6. If another member in the list matches the highlighted member, select it.
7. Choose an action:

- **Join selected member**

Moves the highlighted member to the group with the selected member. Changes the match status for the highlighted member to 40 [Approved].
- **Make [highlighted member] unique**

Assigns the highlighted member a match status of 60 [Unique].
- **Open this list in a new tab**

Displays the highlighted member and the possible matches for it in a new Matching Results tab.

The Matches dialog closes and the Matching Results tab updates with your changes.

View Possible Matches processes the selected member using the matching strategy. For more information, see [Viewing other possible matches for a member](https://support.profisee.com/wikis/profiseeplatform/view_other_possible_matches_for_a_member).