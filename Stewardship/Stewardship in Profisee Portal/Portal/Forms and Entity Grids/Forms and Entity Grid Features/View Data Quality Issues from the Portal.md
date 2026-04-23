# View Data Quality Issues from the FastApps Portal Entity Grid

When you are working in FastApps Portal, you are able to see if records of a given entity have any data quality issues by looking at the Data Quality Status column in the entity grid. The Data Quality Status column (indicated by a black exclamation point) is the first column in any entity grid that has been configured to display the Data Quality Status column.

If the Data Quality Status column does not appear on the entity grid, you may need to request that the Presentation View associated with that entity be changed to enable the display of this column. Refer to [Edit a presentation view](https://support.profisee.com/wikis/profiseeplatform/edit_a_presentation_view) for details.

The Data Quality Status column indicates a data quality issue with a red exclamation point.

This symbol indicates that the record has failed validation and there may be one or more issues associated with that record.

To view the details of the data quality status, click the exclamation point icon. The **Data Quality Status** pop-up dialog opens.

The **Data Quality Status** pop-up dialog displays the status of each attribute on which a data quality rule has been defined. The list of attributes are ordered first by invalid attributes and then by attributes that have passed validation. Within each of these groups, the attributes are ordered alphabetically. Close the dialog by clicking the **OK** button.

## See Also

[Viewing Data Quality Issues from a Portal Form](https://support.profisee.com/wikis/profiseeplatform/viewing_data_quality_issues_from_a_portal_form)

[Presentation Views Overview](https://support.profisee.com/wikis/profiseeplatform/presentation_views_overview)