# Create an Archiving Strategy

An archiving strategy can include data for the entire model or for a portion of the model. If there are only one or two entities in your model that change frequently, you can archive those entities on a regular basis, and use a different strategy to archive the rest of the model data on a less frequent basis.

To create an archiving strategy:

1. In the navigation panel, under Administration, click **Data Archiving and Deployment**.
2. On the Data Archiving and Deployment tab, click **Archive Data**.
3. In the toolbar, click **New**.
4. In the **Name** field, type a name for the strategy.
5. Optionally, select **Filter by Last Updated On** to archive member data according to the date of the last update, and then configure the filter.

1. From the filter operator list, select the operator to use:
- **Is less than**

Selects data updated before the filter date
- **Is greater than**

Selects data updated after the filter date
2. In the filter time and date field, type a date value, or select a date value from the calendar.
3. In the filter time and date field, configure the time value.
6. Using the model tree, select the model objects to include in the archive.

Note: If the archive must include dependent data (such as entities referenced by DBAs) to support your selections, these objects are automatically included in the strategy when they are not already selected. A pop-up message notifies you when these automatic selections occur.

- All objects beneath a selected node are also selected and included in the archive.

This includes any objects that are added in the future. For example, if you select an entity, all of the attributes for that entity will be archived. Any attributes added to the entity in the future will also be archived when the strategy next processes.
- If you do not want to select all objects below a particular node, expand the object and instead select individual objects beneath it.

When there are explicit selections beneath a parent object, only the objects present at that level when the strategy was created are archived. Any additional objects added in the future to the same level will be ignored when the strategy runs. When you make explicit selections on lower-level model objects, the upper-level object names appear in bold, and the check boxes for those objects are no longer selected.
7. When you have finished making selections, click **Save and Close**.

File attribute data cannot be included in an archive and does not appear in the model tree.

Other components, including business rules, views, lists, and strategies can be exported separately using the export tools for the specific feature areas, or by using the Command Line Utility.