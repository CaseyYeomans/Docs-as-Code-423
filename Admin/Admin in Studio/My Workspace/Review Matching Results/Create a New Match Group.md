# Create a New Match Group

When reviewing matching results, it is likely that you will find at least a few proposed members in match groups where they do not belong. One method you can use to correct this is to create new match groups for the mismatched members.

Creating a new match group removes the source record from the original match group and creates a new group with a new group ID. The match group is assigned the next group ID available. When you create a new group using multiple members, they are assigned a match status of 50 {User Mapped}. When you create a group containing only one member, it has a match status of 60 {Unique}.

To create a new match group:

1. Open a Matching Results view tab. For more information, see [Viewing matching results](https://support.profisee.com/wikis/profiseeplatform/view_matching_results).
2. Select a member in the top grid to display the associated match group in the bottom grid.
3. Select the member (or members) in the bottom grid that you want to move to a new match group.
4. Click **Create New Group** on the bottom grid toolbar to create the new group.
5. Click **Yes** to confirm creating the new group.

The new match group is created and is pinned in the third data grid for review. The Match Status for the group members changes to **50 {User Mapped}**, or **60 {Unique}** for groups containing a single member. The original match group remains in the middle grid. The members that you moved no longer appear in the original match group.