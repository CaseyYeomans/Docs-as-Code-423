# Filter: Free-form Control

The free-form filter control allows users to filter using any custom value.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i95b8034fe7dc2d66.png)

* **Name**: Administrative reference name (not visible to end users).
* **Label**: User-friendly display name shown in the portal
* **Input Mode:** Select how users interact with this filter.
  + **Text Input**: For text attributes, allows string-based filtering
  + **Numeric Input**: For number attributes with configurable decimal precision
  + **Date Picker Input**: For datetime attributes with optional time inclusion
* **Decimal precision**: The number of decimal places to display.
* **Include time**: Select this option when filtering datetime attributes that include time. After selecting the date to use in the filter, users can also enter a value for the time.

Filter controls must be linked to other controls to perform filtering actions. Unlinked filter controls will display but won't perform filtering. Input mode selection should match the target attribute type for proper functionality.

---