# View Match Clusters in Survivorship View

Survivorship includes both promotion and harmonization steps. These steps can be accomplished separately, and manually, as described in [Promotion and Harmonization in FastApps Portal.](https://support.profisee.com/wikis/profiseeplatform/mastering_and_harmonization_in_portal) As a data steward, you work with individual records using this method.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i673a7fb113619c22.png)Each record contains a Match Status that describes the initial matching results. These statuses include:

- **Approved**: Record is approved by a user.
- **Auto-Approved**: Record was automatically approved by Profisee.
- **User-Mapped**: Record has been moved into this match cluster by a user.
- **Proposed**: Records match above the Match Threshold, but require user review to confirm a match.
- **Unique**: Record has no similar matches.
- **Unmatched**: Record is unprocessed by the matching strategy or excluded by match criteria.
- **Rejected**: Record is rejected by the matching strategy.
- **Golden Record**: Record to which other records are matched.

## Survivorship Actions not Available

If survivorship is disabled in the Match Group control, the Survivorship tab is not selectable. This can occur for the following reasons:

- The current user does not have the necessary permissions to run survivorship.
- The subject record has a match status of Unique or Unmatched, and therefore survivorship does not apply to it.
- If enabled, the Promote and Harmonize options are only available when the value of the selected attribute differs from the attribute within the Golden Record. If all records in a group have the same attribute values, there is nothing to promote or harmonize.
- The matching strategy does not include the survivorship component.
- The matching strategy has explicitly disabled the survivorship option for the web portal.

If the strategy includes a **Harmonization action policy**, but the **Promotion action policy** is set to **None**, a golden record will not be created when applying survivorship. The strategy may also specify a Promotion action policy, but have no Harmonization action policy.

## Edit Record from Survivorship View

While in survivorship view, you can edit the details of a record within the match cluster.

- Select the eye icon to open the record.
- Within the form, edit information in any available field.
- Click **Save** or **Save & Close** to confirm any changes.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i598730c6686be677.png)

### See More

- [Group Survivorship in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/group_survivorship_in_portal)
- [Promotion and Harmonization in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/mastering_and_harmonization_in_portal)
- [Approve and Reject Match Group Records](https://support.profisee.com/wikis/profiseeplatform/approve_and_reject_match_group_members)