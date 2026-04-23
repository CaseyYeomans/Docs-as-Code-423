# Using Fabric for  Matching Stewardship

Once your data product is associated with complete entities, you can perform basic matching stewardship tasks directly within Fabric. The interface operates as a lightweight version of the Profisee Portal, and many of the actions that can be performed are similar in function and scope.

To access Matching Stewardship, navigate to the entity grid for a connected entity in Microsoft Fabric. Click the **Match Cluster** hyperlink on an entity for which you want to perform matching tasks.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic431d5c7691b8a37.png)

From here, the **Match Cluster Control** view opens. In this view, each record contains a Match Status that describes the initial matching results. These statuses include:

- **Approved**: Record is approved by a user.
- **Auto-Approved**: Record was automatically approved by Profisee.
- **User-Mapped**: Record has been moved into this match cluster by a user.
- **Proposed**: Records match above the Match Threshold, but require user review to confirm a match.
- **Unique**: Record has no similar matches.
- **Unmatched**: Record is unprocessed by the matching strategy or excluded by match criteria.
- **Rejected**: Record is rejected by the matching strategy.
- **Golden Record**: Record to which other records are matched.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i13217267b00c64c7.png)

Records that are not in a match cluster show (Unmatched) and cannot be opened.

## Edit Record from Survivorship View

While in survivorship view, you can edit the details of a record within the match cluster.

- Select the eye icon to open the record.
- Within the form, edit information in any available field.
- Click **Save** or **Save & Close** to confirm any changes.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i454e82a85582ebed.png)

You can also click the **Trash** icon to delete the record, or the **Check** icon to manually approve the record.

### See more

Once you have accessed matching in Fabric, the processes for matching stewardship are the same as in Profisee Portal. Click the links below for information on specific matching stewardship processes. Note that the articles under "Split/Combine Tab" do not apply to Fabric.

- [Promotion and Harmonization](https://support.profisee.com/wikis/profiseeplatform/mastering_and_harmonization_in_portal)
- [Group Survivorship in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/group_survivorship_in_portal)
- [Approve and Reject Match Cluster Records](https://support.profisee.com/wikis/profiseeplatform/approve_and_reject_match_group_members)
- [View Similarity](https://support.profisee.com/wikis/profiseeplatform/view_similarity_in_fastapps_portal)
- [Merge Records](https://support.profisee.com/wikis/profiseeplatform/merge_in_portal)