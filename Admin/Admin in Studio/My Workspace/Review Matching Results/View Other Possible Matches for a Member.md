# View Other Possible Matches for a Member

When you review matching results, you may find members that matched more than one group (Match Multigroup = 1) above the matching threshold. This situation can occur when the matching engine finds two groups that a member could potentially match. The matching engine selects one group and places the member in it, and the Match Multigroup control attribute indicates that the member could match at least one other group.

**View Possible Matches** allows you to view all of the members that matched above the matching threshold for any member. You may find that the second or third-best match is where the member really belongs.

To view potential matches for a member:

1. View members and groups in the Matching Results tab.
2. In the top grid, right-click the member that you would like to see other matches for.
3. Click **View Possible Matches** on the menu.

The Matches dialog appears.
4. Select a match, if applicable.
5. Choose an action. The options that are available depend on your selections and the match status of the highlighted member, but can include:

- **Approve match**

Approves the current match for the highlighted member. Changes the match status of the highlighted member to 40 [Approved].
- **Reject match**

Rejects the current match for the highlighted member. Changes the match status of the highlighted member to 70 [Rejected]. Rejected members keep the Group ID for the original match and continue to appear in that group until reassigned. These options are not available for an unmatched member.
- **Join selected member**

Moves the highlighted member to the group containing the selected member. Changes the match status for the highlighted member to 40 [Approved].

Note: You must select a member in the list with a different group ID than the highlighted member before this option displays.
- **Make [highlighted member] unique**

Moves the member to a new group and assigns a match status of 60 [Unique] to the highlighted member.
- **Open this list in a new tab**

Displays the highlighted member and the possible matches for it in a new Matching Results tab. This is helpful when you spot other members in the results that you would like to regroup without losing your current working list of members for review.

The Matches dialog then closes, and the Matching Results tab updates with your changes.

You can also match new, unmatched members using this procedure. For more information, see [Matching unmatched members](https://support.profisee.com/wikis/profiseeplatform/match_new_members_incrementally).

Attribute set criteria apply to potential matches displayed using View Possible Matches. Strategy criteria (configured on the Matching tab of the strategy) are not applied to View Possible Matches results.

If you see too many identical members returned whenever you use View Possible Matches, ask your Profisee administrator to change the Profisee Server System Setting "Matching lookup include duplicates" from 1 to 0. This change will exclude exact matches from View Possible Matches results.