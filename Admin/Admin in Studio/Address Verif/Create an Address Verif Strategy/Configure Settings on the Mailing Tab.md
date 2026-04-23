# Configure Settings on the Mailing Tab

To configure this tab, you must first complete the required information on the [Strategy Tab](https://support.profisee.com/wikis/profiseeplatform/configure_address_settings_on_the_strategy_tab).

## Before you Begin

Use the Mailing tab to configure input and output attributes and statuses for processing results. If you have licensed location verification and you are working with low-confidence data, you can use location verification to improve the quality of your data sets before executing a strategy using mailing verification.

Map the source and output values for each item in the Field column (for example, Address Line 1, City/Locality, State) defining a location. The source and output fields are selected for mapping according to the model context indicated on the Strategy tab.

- **Fields** are names of discrete data responses from the verification service. Attributes in the entity must be selected to hold the responses included in these fields, or the information will not be retained.
- **Source** attributes contain the source address data to be verified.
- **Output** attributes hold the standardized or improved address information returned from the service is published. You can create the Output attributes during the strategy definition step.

Make sure that the source and output for each field item use separate attributes. If you use the same attribute for the source and output data, then Address Verification will overwrite the existing values. For legacy tracking purposes, this is not recommended.

The **Verification Results** and **Verification Status** fields are required and must be mapped to attributes. Create new attributes to hold this data, if possible. You must map attributes for these items before you can save the strategy.

## Attribute Assistant

Using the Attribute Assistant is the easiest way to complete the attribute selections on the strategy definition tabs. The Attribute Assistant automatically identifies source and output attributes based on the system model.

The Attribute Assistant includes the option to automatically create output attributes based on your selections and the field name. This option is faster than manually creating and selecting an entity attribute for each output attribute.

To use the Attribute Assistant:

1. Click **Attribute Assistant**.
2. In the Attribute Assistant dialog, do one of the following:

Select **Select existing attributes** to use attributes that already exist in the model.

**--or--**

Select **Select existing and create new** to use existing attributes and create new ones when appropriate existing attributes are not found.
3. Select **Use location output attributes as mailing source attributes** to use location output data as mailing address input data (optional).

Using this option is recommended when location verification is available. Using location output data as input for mailing address verification has the advantage of standardizing the address for mailing verification, and prevents sending data for mailing address verification that the location service has already indicated cannot be verified.
4. For Melissa Data users:

Select **Select geocoding output attributes** to include Melissa Data geocoding responses in your verification information (optional).

Note: The output Melissa Data geocoding fields display on the Mailing tab whether or not this option is selected. Select this option to automatically create and use the attributes in your verification strategy. Your Melissa Data license must include support for geocoding to use this feature.
5. Click **OK**.
6. Check the selected attributes and edit them, if necessary.

If you want to include the suite in output of Address Line 1 or Line 2, then select the appropriate **Output Format** (Append Suite/PMB) on either field.

## Options

- Click **Options** and select **Only attempt to verify if location is verified** to avoid attempting to further verify non-existent location information. This option is available when you also have a location verification service provider.
- Select a **Default Country** if you have a large number of addresses located in the same country but no country attribute populated in your data.

## Edit Result Mappings

You can map verification service result codes on the Mailing tab. For more information, see [Edit Result Code Mappings](https://support.profisee.com/wikis/profiseeplatform/edit_result_code_mappings).