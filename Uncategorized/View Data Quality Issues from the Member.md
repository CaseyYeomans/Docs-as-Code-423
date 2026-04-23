# View Data Quality Issues from the Member Details Panel

View the data quality status of a selected member in the **Data Quality** pane.

The Data Quality pane displays the status of each attribute that has a rule defined. The attributes are separated into two groups. The first group is the attributes that have data quality issues. The second group is the attributes that passed validation. Each group is ordered by attribute name in ascending order.

Attributes that failed validation display the full rule clause associated with the failure. The full rule clause contains the following information:

- The name of the attribute that failed validation preceded by a red exclamation point.
- The current value of the attribute.
- The assertion associated with the clause (e.g. **must equal**).
- The value of any constant parameters required by the assertion type -or- the name and value of any attribute parameters required by the assertion type.
- The text of the condition associated with the clause if one exists.

Attributes that passed validation display only the attribute name preceded by a green checkmark.

The figure below shows a sample layout of the Data Quality pane:

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i24e86f398fbc0f1d.png)

The Data Quality pane appears beside the History pane. A resizing bar allows you to adjust the size of each to allow you to focus on the information of interest.

## Viewing data quality issues on secured attributes

The Data Quality pane ensures that security settings associated with a user are obeyed. The following aspects of a rule may involve attributes that are secured and not accessible to certain users:

- Attributes to which the rules are associated.
- Attributes used as parameters in rule clauses.
- Attributes that appear in the conditions associated with rule clauses.

The figure below shows how secured attributes are handled for each of the cases above:

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-idb9c7c6910ff7600.png)

## See Also

[Viewing Data Quality Issues from the Member Window](https://support.profisee.com/wikis/profiseeplatform/view_data_quality_issues_from_the_member_window)