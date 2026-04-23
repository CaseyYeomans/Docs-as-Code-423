# Survivorship Tab

The Survivorship process in Profisee consists of two optional processes: promotion and harmonization. Promotion creates and populates representative group records based on sets of attributes with corresponding rules, while harmonization updates group record attributes with values from the golden records. You can use promotion and harmonization separately, together, or not at all, depending on your requirements.

Complete the information on the Control and Attributes tabs to enable survivorship in a matching strategy. A third tab, Options, provides additional control attributes and settings that you may find useful, especially if you are accustomed to using matching in earlier versions of Profisee.

## Control Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia77326c17912454d.png)

The control attributes hold the values for information returned from the matching process. Click **Attribute Assistant** to check for available attributes, or click each to select or create them manually.

- **Golden Record**--A recursive domain-based attribute used to map match group records to golden records. Golden records are only created during survivorship.
- **Approved count**--A numeric attribute used to store the count of approved records within each match group. This approved count consists of records with AutoApproved, Approved or UserMapped status.
- **Proposed count**--A numeric attribute used to store the count of records with Proposed and Rejected match statuses in each match group.

## Attributes Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id6be6a82a94ffc18.png)

You can create multiple attribute sets in order to promote and/or harmonize different attributes using different criteria.

To define the survivorship process for a strategy, follow the steps below for each set of attributes:

1. Click **New** to create a survivorship attribute set.

The Survivorship Attribute Set window opens.
2. Enter a name for the new attribute set. The default name for the first attribute set is "Set1."

**Attributes Tab**

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ifc34898f889a6a18.png)

The attribute tab allows you to add attributes to an attribute set. This attribute set determines which attributes will be considered for survivorship.

3. Select one or more attributes from the **Available Attributes** list and add them to the **Selected Attributes** list, either by double-clicking the attribute name or by clicking the arrows to move selected attributes between the panes.

You can create additional attributes sets as needed by repeating the above steps. You can keep the default set names, or customize the names to help you rerecord what actions they perform. You can select the sets from the list to edit or delete them. You can use the same attribute across multiple attribute sets.

If the Apply Nulls checkbox is selected, the attribute will be copied into the golden record regardless of value. If it is not selected, blank attributes will not be copied into the golden record.

When the appropriate harmonization and promotion options are enabled, all existing attribute sets are processed when the corresponding strategy is processed.

**Filters Tab**

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5f7c1aa24626db6d.png)

The optional Filters tab allows you to define a filter to isolate the records which will be considered for promotion.

4. Navigate to the Filters tab.
5. Construct a filter by defining the following fields:

- **Attribute**--The attribute to be filtered
- **Operator**--The condition the attribute must adhere to
- **Value**--The target the attribute must meet

**Example**: Size (attribute) must be greater than (operator) 5 (value).

6. If desired, click **Insert** to add a new condition to the filter.

Ifentering additional rows, designate them as **And** or **Or**. If a row is designated as And, the filtered results adhere to both criteria. If a row is designated as Or, the filtered results adhere to either criteria.

7. If desired, select multiple rows and click **Group** to merge them. If you want to separate those rows, select a group and click **Ungroup**.

**Sort Tab**

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3e586143e820bb9a.png)

The optional Sort tab allows you to prioritize records for promotion.

8. Navigate to the Sort tab.
9. Select one or more attributes from the **Available attributes to sort** field.
10. Highlight an attribute in the **Sort properties of selected attributes** field and use the arrow buttons on the right to order the listed attributes by priority.
11. Click the Sort Order dropdown in an attribute row and select Ascending or Descending.

Ascending order prioritizes the lowest value of the selected attribute. Descending order prioritizes the highest value of the selected attribute.
If the defined sort causes multiple records to tie for the highest priority, the final tiebreaker can be configured on the Configuration tab.

**Configuration Tab**

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5e8afd0d8923f6.png)

The Configuration tab allows you to configure promotion and harmonization for this attribute set.

12. Navigate to the Configuration tab.
13. Select one of the following from the **Promotion Action Policy** list. This specifies when the golden records should be updated. Each survivorship attribute set must have at least one harmonization or promotion action policy or you will not be able to save the strategy.
- **None**--Golden records will not be updated. Use this option if you only want to harmonize source records with this attribute set, or if you want to temporarily disable promotion for the selected attribute set.
- **Only copy if the attribute is blank**--Populate golden records from the source records only if the golden record attribute value is blank. All blank values will be set, and the populated values will not be overwritten.
- **Only copy if all attributes are blank**--Populate golden records from the source records only if all attribute values in this set are blank in the golden record.
- **Always copy (overwrite)**--Always update the golden record attributes regardless of the golden record attribute values.
14. Optionally specify a Promotion condition that further controls which golden records are updated. This condition acts as a filter and lets you check for a specific attribute value, string criteria, date, or numeric range to determine whether to update the golden record.
15. Specify the promotion criteria.

The promotion criteria are used to determine which group record is used to update the golden record attributes in this set. Configured promotion criteria are evaluated in order until a single group record matches. If all group records are equally good candidates after all criteria are evaluated, Record recency, which is always selected by default, is used as the tiebreaker.

Null attribute values are not used to update golden record attribute values when all promotion attributes are null. However, if some of the promotion attributes are populated and some are null, then null values can be survived in the golden record.

Select any of the following from the **Promotion criteria** table to specify which source records will be used to update the golden records.

- **Record completeness**--Selects the group record with the most populated attribute values.
- **Value occurrence**--Selects the record with the attribute values appearing with the greatest frequency in group records. Note that distinct values are found for the complete attribute set, not for individual attributes. Attributes must be split out separately (in separate attribute sets) if independent evaluation is required.
- **Record recency**--Automatically selected option used as the tiebreaker if multiple records meet the above promotion criteria equally. The record recency is determined by the record date/time stamp in Profisee. You can choose either to select the "Newest" or "Oldest" record, and determine the date used by selecting either "Created on" or " Last updated on" audit attributes.

The matching process changes the last updated time and date for matched records. Therefore, when matching and survivorship run together, recency with Last Updated On selected becomes a random way to select a record to provide survivorship data. It is not possible to determine ahead of time which record will be processed first or last.

If multiple of these options are used together, the order in which they are implemented is: Filter and Sort > Record Completeness > Value Occurrence > Record Recency.

16. Specify the harmonization action policy.

Define a harmonization condition if you want to update the source record attributes from the golden records. Harmonization is optional and may not be appropriate for environments where source systems do not have access to the harmonized data.

Select one of the following options on the **Harmonization action policy** menu. This selection specifies when the source records should be updated or harmonized from the golden record attributes for this set.

- **None**--Group record data will not be updated. Use this option if you want to only golden record source records with this attribute set.
- **Only copy if the attribute is blank**--Populates the attribute in the group record only if it is blank
- **Only copy if all attributes are blank**--Populates the values in the group record from the golden record if all attribute values in this set are blank for that record
- **Always copy (overwrite)**--Always update the group record attributes with the specified golden record attribute values
17. Optionally specify a **Harmonization condition** that further controls which group records are updated. This condition acts as a filter and lets you check for a specific attribute value, string criteria, date, or numeric range before updating group record data from the golden record.
18. Click **Save** to save your survivorship attribute set.

## Options Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3d443d94fb75eb39.png)

Configure the following optional settings to change the behavior of survivorship. Survivorship options apply to survivorship performed both during batch processing and interactively except where indicated.

- **Create and update golden records for unique records**--Create golden records for unique records. Creating golden records for unique records lets you treat unique records and records in match groups consistently, as every source record has a golden record.Golden records for unique records appear in the list of Match Groups with only one record (the unique record).
- **Only update groups that have changed since last run**--Apply survivorship only to groups where one or more control attributes, survivorship attributes, or attributes used in the promotion criteria have changed since the last processed transaction. Applies to batch processing only. Changes to multi-level attributes are not detected.
- **Update counts on golden records after survivorship**--Adds or updates statistics for match groups on the golden record for the number of approved and proposed records in the group. When this option is cleared, these counts are blank for the group.
- **Golden record code format:**

- **Prefix**--The character string that will prefix each golden record. Use the default "GoldenRec-" value, or specify a different prefix up to 10 characters. This prefix is used to create a unique code for golden records.
- **Base**--Select **Group ID** to generate golden record codes based on the Group ID. For example, with a prefix of "Golden Record-" and a Group ID of 075, the golden record for that group would have the code Golden Record-075.
- **Special grouping records (optional)**

Completing the following options creates two special records during matching.

- **Golden Record code**--Use the default value or enter a custom value to use as the code for the Golden Record's special record. This golden record is used as the attribute for golden records of match groups.
- **Uniques code**--Use the default value or enter a custom value to use as the code for the Uniques special record. This Uniques record is used as the main attribute for unique records.