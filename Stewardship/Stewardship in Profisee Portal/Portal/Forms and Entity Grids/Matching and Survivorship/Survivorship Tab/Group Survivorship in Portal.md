# Group Survivorship in FastApps Portal

Survivorship includes both promoting and harmonization steps. These steps can be accomplished separately, and manually, as described in [Promoting and Harmonization in FastApps Portal.](https://support.profisee.com/wikis/profiseeplatform/mastering_and_harmonization_in_portal) As a data steward, you work with individual records using this method.

| | |
| --- | --- |
| | **Apply Survivorship to the Cluster** |

Group survivorship is performed automatically, based on the survivorship strategy created by your administrator. To perform group survivorship in Portal:

1. Open the [Match Cluster control](https://support.profisee.com/wikis/profiseeplatform/accessing_match_cluster_controls) for the desired Match Group and navigate to the Survivorship tab.
2. Click the **Apply survivorship to the cluster** icon. The strategy works in the background according to the parameters and thresholds set by your administrator.
3. Survivorship runs for the currently displayed group. A **Processing**message window displays. Additional actions cannot be performed until processing is complete.
4. Survivorship processing is complete when the **Processing**message window closes.

Group records now display updated information.

- If the group had no golden record before, a golden record may be created if specified in the strategy (see note below).
- Any promoting and harmonization rules run and record data are updated accordingly.

If the Survivorship icon is disabled, see [Availability of survivorship in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/availability_of_survivorship_in_the_web) for possible reasons.