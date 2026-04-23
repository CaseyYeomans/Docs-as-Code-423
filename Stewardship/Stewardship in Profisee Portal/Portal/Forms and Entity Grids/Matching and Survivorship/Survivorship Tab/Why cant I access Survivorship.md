# Why can't I access Survivorship?

Survivorship is disabled in the Match Cluster control if the Survivorship icon is not enabled. This can occur for the following reasons:

- The current user does not have the necessary permissions to run survivorship
- A golden record or match cluster record is selected for editing
- The subject record has a match status of Unique, and therefore survivorship does not apply to it
- A cluster record displays the golden record and harmonize icons only when the value for the selected attribute differs from the value in the cluster golden record.
- The matching strategy does not include survivorship configuration
- Web survivorship is disallowed by the strategy configuration
- All records in a cluster have the same attribute values, meaning that there is nothing to promote or harmonize