# Reject a Match

When you review matching results, it is likely that you will find proposed records in match groups where they do not belong. The 30 {Proposed} match status indicates that the record could potentially be a match, but the match score is low enough that the match requires manual review.

If the record is not correctly grouped, you can reject the match. Rejected records remain in the match group where they were placed during processing and are assigned a match status of 70 {Rejected}.

Assigning the Rejected status to a record is not necessary if you want to move a record to a new group immediately. However, the Rejected status is useful if you want to mark a match as invalid without having to immediately find a better group for it. You can filter the records on Match Status to locate the rejected records when you have finished reviewing matches and work with them as a group.

To reject a match:

1. Open a Matching Results view tab. For more information, see [View Matching Results](https://support.profisee.com/wikis/profiseeplatform/view_matching_results).
2. Select a record in the first grid.

The records in the corresponding match group display in the bottom grid. If survivorship has been run, the golden record displays in the first (gold shaded) row followed by all source records mapped to that golden record. The Match Status column displays the 30 {Proposed} status for records requiring approval.

1. In the bottom grid, select the match group record you want to reject.
2. Do one of the following:

Right-click the record and then click **Reject Match** on the menu.

**--or--**

Click **Reject** on the bottom grid toolbar.

5. The record remains in the group with a status of 70{Rejected}. The match status of 70 {Rejected} makes it possible to filter records for rejected records and to process them further as necessary.

To find alternative match groups or create a new group, see the following:

[Find Similar Records](https://support.profisee.com/wikis/profiseeplatform/find_similar_members)

[Create a New Match Group](https://support.profisee.com/wikis/profiseeplatform/create_a_new_match_group)

[View Other Possible Matches](https://support.profisee.com/wikis/profiseeplatform/view_other_possible_matches_for_a_member)