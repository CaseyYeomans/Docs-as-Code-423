# Configure the Filter Control

The Filter control lets you create a filter on a portal application page which you can then connect to an entity grid control or another Filter control.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia80484c842be063.png)

To configure the Filter control:

1. Follow the instructions in [Add a New Portal Application Page](https://support.profisee.com/wikis/profiseeplatform/add_a_new_portal_application_page), adding a Filter control.
2. Under Properties, enter a name for the filter control in the **Name** field.

The Name field is for administrative reference only and does not display to users when the control is viewed in the portal.

3. Enter a descriptive, user friendly name for the filter control in the **Label** field.

The label displays to users when they view the control in the portal. Other names for controls are available for reference during configuration only.

4. Select one of the following options:

- Domain-Based Attribute Filter
- Free-Form Attribute Filter

After the filter control is configured, it must be linked to another control. If it is not linked, the control will display in the portal application page, but it will not perform any filtering actions. For more information on linking the filter control, see [Link Controls](https://support.profisee.com/wikis/profiseeplatform/link_controls).

#### **Domain-Based Attribute Filter**

A domain-based attribute filter lets you configure a filter for a domain-based attribute. Users can filter the entity by selecting the values in the selected attribute.

This setting controls the way that DBA values are displayed to portal users in the filter control. Choose from the following methods:

1. From the Domain entity list, select the domain entity containing the values to use in the filter.
2. From the Drop-down format menu, select the way the domain values display in the filter when viewed by portal users. Possible selections include:
- Code
- Code [Name]
- Name
- Name [Code]
3. Select the DBA input mode. This setting controls the way that DBA values are displayed to portal users in the filter control. Choose from the following methods:

- **Dropdown Input:**A scrollable dialog list is displayed for up to the first 50 domain values. The user can type a value into the field to search or use the filter icon to display a popup dialog that allows for viewing and searching all domain values.
- **Visual (chart) Input**: Creates a [Visual Filter](https://support.profisee.com/wikis/profiseeplatform/using_visual_filters) on the page that allows users to view and filter records on this page. The user can select the dropdown to select one of five types of charts to use for the visual filter.
- **Text input:**Selecting this option will not display a dropdown list or enable the filter popup, but provides a search criteria field and a text field to allow the user to type the value they want to use to filter an attribute instead of selecting an existing domain value from a list. When a user enters a value, both Name and Code values for the receiving attribute are searched.

#### **Free-Form Attribute Filter**

A free-form attribute filter lets users filter a free-form attribute in an entity grid with any value that they choose to enter.

It is important to select the correct input mode for the type of attribute that the filter control will be linked to. For example, if the filter will be used with a date attribute, it will require that users enter data in the correct format for dates, so be sure to select the date picker input mode.

- **Text input mode:**Select this option when the filter control will be applied to a text attribute. Users can type text strings into the filter to constrain the displayed data.
- **Numeric input mode:**Select this option when the filter control will be applied to a number attribute. Users can type numeric data into the filter to constrain the displayed data.
- **Decimal precision**: Enter the number of decimal places to display.
- **Date Picker input mode:** Select this option when the filter control will be applied to a datetime attribute. Users can type in the date, or pick the date to use in the filter from a pop-up calendar.

- **Include time:** Select this option when filtering datetime attributes that include time. After selecting the date to use in the filter, users can also enter a value for the time.