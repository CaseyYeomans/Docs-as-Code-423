# Configuring the Matching Sets Tab

To create a new Matching Set, click the **+** icon on the **Matching Sets** table.  Multiple sets can be used with different minimum matching criteria to handle blank attribute values and different matching scenarios.

Each set represents the minimum matching criteria. Start with one attribute, and if there is over-matching, add another. More attributes result in fewer matches being found.

> [!NOTE]
> • For best performance, the first attribute in the set should be the one with the most distinct values. • Do NOT use a single set with multiple attributes with "Ignore blanks" to handle blank values. • Do NOT use "Ignore Blanks" on the first attribute set. Doing so may decrease performance. • Do NOT build descending sets with the same 4 attributes, then 3, then 2, etc. Each set should have the minimum required attributes to make a match. If 2 are the minimum, then 4 and 3 are redundant.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3812d8f6e43ec84f.png)

Creating a new matching set causes the **Matching Attribute Set** pane to open. From here, you can configure settings for the matching set and add or remove attributes from the set.

1. Enter a name for the attribute set.
2. Determine the **Auto-Approve Threshold**. Potential matches that meet this threshold are automatically approved.
3. Optionally create a filter for the **Feature Set Criteria**, allowing you to limit which records are processed in the set.
4. Select attributes from the Available Attributes list on the left panel to be moved into the **Selected Attributes** panel.
5. Configure settings for the selected attributes.
   * **Match Type**: Select one of the available match types.
     + **Token**: The value is broken up into three character pieces and matched using a similarity calculation.
     + **Word**: The value is broken up into words separated by spaces, and each word is matched regardless of word order.
     + **Exact**: The entire value is matched.
     + **AI - Embeddings**:The attribute values are sent to the configured AI embedding service to generate semantic vector representations [configured as an Aisey model](https://support.profisee.com/wikis/profiseeplatform/creating_a_new_aisey_model)
   * **Threshold**: Determine the matching threshold for the set. Values with scores above this threshold are matched.
   * **Blank Values**: Determine how the attribute set handles blank values.
     + **Exclude blanks**: Records with blank values are excluded from matching in this set.
     + **Group blanks**: Records with blank values match other records with blank values. Records with blank values do NOT match other records with values. Records with a value do NOT match a record with a blank.
     + **Ignore blanks**: Records with blank values match to records with blank or a value. Records with a value do NOT match a record with a blank - if any value can equal null, then different values can match in the same group, which is not allowed.
   * **Synonym List**: Select the previously configured [synonym list](https://support.profisee.com/wikis/profiseeplatform/synonym_lists_in_profisee_portal) to be used for this strategy. (Optional)
6. Click **Save** to create the attribute set.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i36c6ccaccc25cca.png)

---