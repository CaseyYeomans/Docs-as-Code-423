# Entity Grid Control

The Entity Grid control displays entity data in a tabular format with sorting, filtering, and editing capabilities.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6611e8f6eee84308.png)

* **Name**: Administrative reference name (not visible to end users).
* **Entity**: Select the data entity to display.
* **View**: Choose a presentation view to define columns, filters, and sorting. If no view is selected, the grid defaults to displaying Name and Code columns.
* **Add Record Form**: Specify which form is displayed when users create new entity members via this control.
* **Open Record Form**: Specify which form is displayed when users view or edit existing members.
* **Can Delete**: Enable or disable the ability to delete records from this grid. When disabled, this setting overrides user permissions.
* **Matching Strategy**: Select a matching strategy to apply to this entity grid
* **Enable Hyperlink to Match Group Control**: Allow users to click within the grid to navigate directly to match groups
* **Enable Lookup-Before-Create**: Apply lookup validation before allowing creation of new members
* **Prohibit Add if LubC Fails**: Block member creation when lookup validation fails.

> [!CAUTION]
> Lookup-Before-Create will not be enabled (even if selected) if the View does not correlate to a configured Results View on a matching strategy on the same entity. See the page on the Lookup Tab for more information about Lookup-Beofre-Create.

User permissions determine add and edit capabilities regardless of form selection.

---