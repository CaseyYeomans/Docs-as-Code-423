# Data Quality Rules FAQ

The following are answers to frequently asked questions about Data Quality Rules:

- What does this error mean, and how do I "refresh client cache"?

Rule ID # could not be found in client cache when processing, creating invalid attribute for member [member code] in entity [entity name]. Recommend refreshing client cache.

This error indicates that you should close FastApp Studio and reconnect. If the portal is launched, click the **Refresh** button in your portal settings.

- If an attribute value is required, but the source provides only a null and we have an assignment rule for a default value, would that result in a validation error?

Yes initially, but the assignment rule setting the value will cause validation rules to run again on that member, eventually clearing the validation issue.

- I do not get the desired result when blank values come into play. How can I account for this?

In this cases involving blank values, try using an inverse of the rule.

For example; a rule that says 'Name is valid' when first name contains John or last name contains Smith will not work as you may expect for a scenario where first name is Bob and last name is blank.

If you switch this rule to use 'Name is NOT Valid' when first name does *not* contain John or last name does *not* contain Smith, the rule will work as expected.

- What does "Secured issue" mean?

If a user does not have sufficient permissions to view an attribute that has triggered a data quality issue, the issue will be displayed as "Secured issue." If multiple attributes triggered a data quality issue, each attribute that a user does not have permissions to view will be displayed as its own "Secured issue" response.

- Why does my validation status appear as valid even when a rule should make it invalid?

The assignment is evaluated based on the initial validation status before it is evaluated for validity. Therefore, it appears as valid when assignments are evaluated. If you update or save the record again, the assignment processes correctly since the record is now invalid when assignments are evaluated.

- Why do the Created By and Last Updated By statuses reflect the users incorrectly?

Due to a change in 2024.R1, the Created By status reflects the user who created the rule, and the Last Updated By status reflects the prior updating user (not the current updating user.)

To see the information as it was displayed in prior releases, users can use the NOW expression as an alternative.