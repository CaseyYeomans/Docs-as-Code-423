# Configure Settings on the Location Tab

Before you can use location verification, you must include your Bing or Google API key in System Settings. For more information, see [Configuring Bing or Google Location Verification System Settings](https://support.profisee.com/wikis/profiseeplatform/configure_bing_or_google_location_verification_system_settings).

To configure the Location tab, you must first complete the required information on the [Strategy Tab](https://support.profisee.com/wikis/profiseeplatform/configure_address_settings_on_the_strategy_tab).

## Before you Begin

Use the Location tab to configure input and output attributes and statuses for processing location verification results. If you have also licensed mailing verification, you can use location verification to first to scrub your data sets before processing strategy options for the Mailing tab. Using location verification to perform a first pass eliminates non-existent addresses and can complete addresses with missing information before submitting the data for mailing address verification.

Map the source and output values for each item in the Field column (for example, Address Line 1, City/Locality, State) defining a location. Address Verification selects source and output fields for mapping according to your model context, indicated on the Strategy tab.

- **Fields** are names of discrete data responses from the verification service. Attributes in the entity must be selected to hold the responses included in these fields, or the information will not be retained.
- **Source** attributes specify the attributes that contain the source address data to be verified.
- **Output** attributes are the attributes where the standard address information returned from the service is published. You can create these attributes during the strategy definition step.

Make sure that the source and output attributes for each field item are separate. If you use the same attribute for the source and output, then Address Verification will overwrite the existing values for that field. For legacy tracking purposes, this is not recommended.

The **Location Response Count**, **Location Status** and **Location Confidence** attributes are required. Create new attributes for this data, if possible; you must select attributes for these items before you can save the strategy.

## Attribute Assistant

Using the Attribute Assistant is the easiest way to complete the attribute selections on the strategy definition tabs. The Attribute Assistant automatically identifies source and output attributes. It can automatically generate and assign output attributes based on your selections and the associated field names. This option is faster than manually creating and then selecting an attribute for each output attribute.

To use the Attribute Assistant:

1. Click **Attribute Assistant**.
2. In the Attribute Assistant dialog, do one of the following:

Select **Select existing attributes** to use attributes that already exist in the model.

**--or--**

Select **Select existing and create new** to use existing attributes and create new ones when appropriate existing attributes are not found.
3. Click **OK**.
4. Check the selected attributes and edit them, if necessary.

## Manual Configuration

First specify the attributes containing the source data to verify, and then specify the attributes that will contain the strategy results. If you want to skip verification for any field, leave both input and output values for that field blank. If you do not select an attribute for a required field, an error displays when you try to save the strategy. You cannot save the strategy until all required attributes are mapped.

1. Click each attribute in the **Source** column and click the arrow to open the menu.

Select the attribute that is the source for each location item listed in the **Field** column.
2. Click each enabled field in the **Output** column and do one of the following:

**--or--**

- Select the attribute you want to map with each field.
- Select **Create New**. Type a name for the new attribute and then click **OK**.

## Options

The Options menu lets you configure how to handle data in certain situations:

- **Confidence Threshold**: Select the lowest confidence threshold for saving output addresses in batch mode. The location verification service returns a confidence level for each address (High, Medium, Low). During batch processing, the system does not update the output attributes if the confidence value returned from the address service is lower than this threshold. Note that Google results are mapped to High and Medium only; Low is not used.
- **PO Box Regex pattern**: The default pattern is used to find post offices boxes in the United States. For other countries, configure the string to recognize the specific address type. This option allows Address Verification to verify the place (city, state, postal code) portion of the address.
- **Use source data when output unavailable**: Populates the output attributes with source data values if no output data is available.

You must complete the required information for one at least one Field column item in addition to the required Confidence, Location Response Count, and Status fields to save the strategy. If you omit an attribute for a required field, an error displays and you cannot save the strategy.

When you reprocess a strategy using the same set of data, Address Verification overwrites the output attribute values, with the exception of the Status attribute created in the Strategy tab.

For more information, see [Configuring Settings in the Strategy Tab](https://support.profisee.com/wikis/profiseeplatform/configure_address_settings_on_the_strategy_tab).