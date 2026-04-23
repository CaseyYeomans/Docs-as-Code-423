# Promotion and Harmonization in FastApps Portal

As discussed in the [Matching and Survivorship Overview,](https://support.profisee.com/wikis/profiseeplatform/matching_and_survivorship_overview) survivorship includes both Promotion and Harmonization. In simple terms, **Promotion** causes an attribute value from a match cluster record to become the value for the Golden Record, whereas **Harmonization** causes an attribute value from the Golden Record to become to value for all match cluster records.

## Harmonization

Harmonizing is the process of updating match group records with data from the Promote record. There are three ways to perform harmonization: All records, all values, or single value.

### Harmonize All

This method takes all attribute values from the Golden Record and applies it to all records of the selected match group. To Harmonize All, click the ellipsis icon on the Golden Record header and select **Harmonize All**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7d82dcc79e8bf533.png)

### Harmonize

This method takes all the values from a single Golden Record attribute and applies them to a selected match group record. You can Harmonize one or all match group records.

1. To Harmonize only one match group record find the attribute you wish to harmonize with the Golden Record and click the Harmonize arrow icon. This harmonization icon only appears if it contains attribute values that differ from the Golden Record.
.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2917732c57c8e263.png)
2. To Harmonize an attribute for all match group records, Click the harmonization icon on the Golden Record. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib43d5afcb53c1549.png)

## Promotion

Promotion creates or replaces a Golden Record from another record in the match group. The Golden Record can be selectively populated with data from representative group records.

There are three ways to Promote:

- Locate the desired source record to be Promoted.
- Locate the desired attribute in the source record.
- Select the desired attribute value from the dropdown menu in the Golden Record.

### Promote All

This method takes the values from all attributes of one record and applies them to the Golden Record.

1. Click the ellipsis icon on the record you want to promote.
2. Select **Promote All** from the menu.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i42a17d6d6535c060.png)

### Promote

This method takes the value of a single attribute in a record and applies it to the Golden Record.

1. Hover over the attribute of a record you want to Promote. The Promote icon appears in the value's field if it differs from the Golden Record.
2. Click the Promote icon. The Golden Record value changes to reflect the value in the record.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i73ad1c2c2f6a6d8c.png)

### Single Value from the Dropdown Menu

You can also change an attribute value of the Golden Record from a dropdown menu on the Golden Record itself. For example, if the Address attribute in the Golden Record is a survivorship attribute, all addresses from all records in the match group will be available in that dropdown. If you know which value is correct, simply select the desired value.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iae864f9ae0c6b920.png)

If you need to make sure the value comes from a specific source system, you might prefer to locate that specific match record and promote that record.

If the Promote and Harmonize icons are disabled or do not appear, see [Why can't I access Survivorship?](https://support.profisee.com/wikis/profiseeplatform/availability_of_survivorship_in_the_web) Availability of survivorship in the Webfor possible reasons.

## See Also

[Matching and Survivorship Overview](https://support.profisee.com/wikis/profiseeplatform/matching_and_survivorship_overview)

[Review Matching Results in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/review_matching_results_in_portal)

[Approve and Reject Match records in FastApps Portal](https://support.profisee.com/wikis/profiseeplatform/approve_and_reject_match_group_members)