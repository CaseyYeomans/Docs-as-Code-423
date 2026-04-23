# Matching Tab

## Attributes Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i97a1d0b7ed0b795.png)

The matching attributes and thresholds configured on the Attributes tab drive the matching process. Matching attributes determine the values that are compared when matching runs. You can create multiple sets of attributes that run sequentially during matching. Configure settings on the Matching tab after completing the settings on the Strategy tab. Note that you cannot match datetime attributes.

To configure settings on the Attributes tab:

1. Click the **Matching** tab with a matching strategy open. The first tab under **Matching** is **Attributes**.
2. Click **New** to create a new matching attribute set.
3. Enter a name for the set in the **Attribute set name** field, or keep the default name.
4. Edit the **Auto-approve threshold** value for the attribute set.

The **Auto-approve threshold** determines whether matching records are automatically approved, or assigned a match status of **Proposed** and flagged for manual review. For example, if the Auto-approve Threshold setting = .90, and a record matches an attribute group during the first step at .90 or higher, then that record is matched with that group and assigned a match status of **AutoApproved**.

5. Configure criteria for the attribute set (optional):

Filter criteria will be applied to records when this attribute set processes, and the records matching the filter will be processed.

1. Click **Attribute set criteria**.
2. Click **New** to add a new filter condition.
3. Select an attribute from the first list to define the attribute to use to filter records.
4. Select the operator for the filter criteria from the second list.
6. Select one or more attributes from the **Available Attributes** list and add them to the **Selected Attributes** list, either by double-clicking or using the arrows to move the attributes between the lists.
7. Modify the following options for each attribute set based on the type of matching results you want:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ida0579f275dda969.png)

- **Match Type**--Select the matching method to use in this step:

For more information, see [Select a Match Type](https://support.profisee.com/wikis/profiseeplatform/matching_concepts).

- **Token**--Match text strings within words. This is the default match type for fuzzy matching which allows for typographical errors and other minor variations in data values.
- **Word**--Match records using whole words. The word can match anywhere in the string value.
- **Exact**--Only match records that are exact matches.

- **Threshold**--Similar records with a match score below this threshold are not matches. Each matching attribute can have a different threshold assignment. The default value is .70, but the threshold can be any value from 0 to 1.0 (an exact match). The average threshold is calculated and used as the bottom score for creating match groups. When a record is matched by an attribute set at the match threshold or higher, the matching process stops for that record, even if additional attribute sets are available. If a record is not matched at the match threshold value or higher, however, then that record is processed using the attributes in the next set.

You may need to change this value and run the strategy several times to understand how this threshold applies to your data.

Generally, you should use a match threshold well above 0.5. The Profisee System Setting called "Matching minimum threshold" controls the lowest possible threshold value.
- **Blank Values**--Select the method for handling blanks:

For more information, see [Match Data Containing Blanks](https://support.profisee.com/wikis/profiseeplatform/matching_concepts).

- **Exclude records**--Filter out records containing blanks for the matching attribute and do not include them in matching. At least one attribute in every attribute set must have this setting.
- **Group blanks**--Group together records with blank values for matching attributes. The attribute match score is set to 1.0 when blank values are compared to each other.
- **Ignore blanks**--Match records based on the other populated matching attributes and ignore any blank values in this attribute. Blank values are considered similar to all other values and are scored at the threshold level for this attribute.
- **Synonym List**--Select the synonym list to use with the strategy from the Synonym Type list. Use synonym lists to improve matching results by decreasing noise and standardizing terms that are unlikely to be unique. For more information, see [Create a Synonym List](https://support.profisee.com/wikis/profiseeplatform/create_a_synonym_list).

While you can use the same attribute in multiple attribute sets, you can only use one synonym list for each attribute across all sets.

8. Click **Save** to save the attribute set.
9. After you have created your attribute sets, you can optionally change their processing order using the arrows to the right of the list. The Order column indicates the order in which the sets are processed during matching.
10. Click Save to save the strategy, or continue to select other tabs to complete additional strategy settings.

## Criteria Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1c8bab4cd6c7ed17.png)

Define optional criteria so the matching process is executed for a subset of the records in the entity. Matching processes only the records meeting the defined criteria.

The Criteria tab contains areas for creating two sets of criteria. The Match-From filter controls which records search for matches, where the Match-To filter controls which records are candidates to be searched.

To filter records using criteria:

1. Select the **Criteria** tab in the Matching strategy.

If you are creating a new strategy, then you must first complete the required information on the Strategy tab.

2. Click **New** to add a new filter condition.
3. Select an attribute from the first list to define the attribute to use to filter records.
4. Select the operator for the filter criteria from the second list.
5. Enter or select a value for the filter criteria in the third list. To filter records based on blank values, leave this field empty.

Selections on the Criteria tab apply to matching only (not to survivorship).

## Options Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i851331954bfac7ac.png)

Define optional settings for matching:

### Batch options

- **Leave unique records as unmatched**--No records are assigned a match status of Unique. Records that do not match any other records are included with the unmatched and excluded records. These unmatched unique records will continue to participate in incremental matching runs.

### Clustering

Customers should choose whether sets have equal value/weight or the higher sets have more value/weight.

In the example strategy below a customer has a two set strategy - Set1 matches on Name+SSN, Set2 on Name+Address.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i11eebb65c0ed968e.png)

- **Prioritize Order of Sets**-- Prioritizes sets based on their order in the strategy. When matches are found on multiple sets, only the highest set is used, since it has priority over other sets.

In the example below, there are two pairs of records matching on Set1, and all four match on Set2.

Using Set Priority, the higher value/weight Set1 is used to form the clusters, and the lower value/weight Set2 is ignored. The secondary match will be used only if there is no higher set match.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie00152329920538d.png)

- **Prioritize Highest Score** -- Prioritizes the highest total match score. When matches are found on multiple sets, all sets have equal value/weight and are used to build the cluster.

In the example below, there are two pairs of records matching on Set1, and all four match on Set2.

Using Score Priority, there is a single match cluster because all sets have equal value and all records are joined. If one set has a higher score, it will be used for the match member, but all matches will be used for clustering.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4ac7596b6543d9e6.png)