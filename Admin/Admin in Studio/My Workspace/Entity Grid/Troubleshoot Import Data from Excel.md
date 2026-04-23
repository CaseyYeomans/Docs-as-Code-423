# Troubleshoot Importing Data from Excel

**Issue**: When importing or exporting data, you see system messages indicating an incompatibility between the operating system architecture and the Excel version (such as a 64-bit operating system running a 32-bit version of Excel). Excel was installed using Office 365.

- Check the Profisee support portal for a workaround.

**Issue**: Data only partially imports

- Excel may automatically assign a data type to a column in a spreadsheet based on the data in the cells. The type is based on the data values appearing in the first several rows of the spreadsheet. If the column values are of mixed types, sort your data so that both strings and numeric data appear in the first few rows. For more information on how Excel determines column types, refer to the Excel documentation from Microsoft.

**Issue**: Formatting from Excel spreadsheet cells is lost on import

- Leading and trailing spaces and carriage returns are automatically stripped from imported Excel data. Carriage returns in the middle of cells remain but do not display in Profisee. Excel values containing carriage returns imported to Profisee will appear to run together. When exported back to Excel, the data displays carriage returns normally.

**Issue**: When importing data, clicking Create new attributes results in multiple system messages regarding reserved words.

- If you exported entity data to Excel, made changes, and then imported data to Profisee from the same spreadsheet, you may see messages regarding attributes with the same names as reserved words. This occurs when you try to create attributes for the audit columns, which Profisee ignores by default. You cannot create new attributes to hold this data because attributes with the same names exist in every entity. The audit attributes include the following:

- Last Updated By
- Last Updated On
- Created By
- Created On

To avoid messages regarding these attributes, make sure these four audit attributes are ignored when you import the data.

**Issue**: New values imported into Excel do not display in the grid after publishing.

- Make sure that the target attribute is not restricted. Data cannot be imported into restricted attributes.
- Make sure your user account has permission to edit information for the attribute.

**Issue**: When importing data to Profisee using Excel 2016, you change between Excel source files and Profisee crashes.

- Make sure you have installed the most recent Office 2016 updates from Microsoft.
- Make sure Access Runtime 2013 is installed. You can download it here: <https://www.microsoft.com/en-us/download/details.aspx?id=39358>.

**Issue**: Error appears: "Unable to open in Excel. Make sure Excel is installed and running."

- This is a known issue for entities with more than 255 attributes. If possible, reduce the amount of attributes in the entity or split them between multiple entities.
- If the above is not possible, try opening in Excel through Profisee FastApp Portal instead. You will need to add all of the columns to your presentation view.

**Issue**: Rows with long character counts are being truncated.

- In some scenarios where values longer than 255 characters are included in an imported Excel spreadsheet, those values become truncated. This issue occurs if an entry with more than 255 characters is *not* included in the first few rows, in which case they are not sampled by the Excel driver.

This can be solved by ensuring a value of 255 characters is added to your first row **OR** by editing the registry and setting the **TypeGuessRows**value to **0**. Note that Windows updates may change this value back to the default of 8.