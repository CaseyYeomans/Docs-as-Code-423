# Downloading and Uploading an Entity Grid as a File

You can easily download data from an Entity Grid to be used in other programs, allowing for offline analysis and modifications or for updating information in bulk in a different program. Afterward, that data can be uploaded to an entity grid from the same file format. Primarily, this function can be used to upload and download entity grid data for use in Excel.

As of 2025.R3, the only compatible file type is .XLSX. Future releases will add additional file types.

## Download an Entity Grid as a File

To download an entity grid as a file:

1. Navigate to an entity grid in Profisee Portal.
2. Click the vertical ellipsis icon and select Download as Excel. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5986df16b8696675.png)
3. The entity grid is downloaded as a .XLSX file.

## Upload File to an Entity Grid

To upload a file to an entity grid:

1. Navigate to an entity grid in Profisee Portal.
2. Click the vertical ellipsis icon and select "Upload from Excel." The *Upload From File* window opens.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4521b3aa08706431.png)
3. Click **Browse** to select a file from your machine.
4. Click **Next**.
5. If needed, select a sheet from the file to be used in the entity. If desired, you can click **Preview** to view the data contained on the selected sheet.
6. Click **Next**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5b2dda5293f65323.png)
7. Use the dropdowns to map the data from your file to attributes in your entity. Items that share a name will be automatically mapped. You can optionally select **Automatically Add DBA Values** to automatically assign Code values to the DBAs. You can also use the f(x) function icon to create an expression to populate the attribute. This expression must return a type compatible with the selected attribute (such as Date or Number).
8. Once all attributes are mapped, click **Run** to add the data to the entity grid.![Image](https://profisee.visualstudio.com/ad098ab8-fc30-4fe4-982d-460e6c9eb694/_apis/wit/attachments/8b8199da-cf7c-49aa-be94-eedd749f7d07?fileName=image.png)

A known Excel bug where dates from the year 1900 or earlier may appear shifted to the next day may impact the way old dates are displayed in Profisee Portal if imported from Excel. For example, a date input in Excel as 1/1/1900 may appear as 1/2/1900. For more information on this issue, see [this article](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/excel/wrongly-assumes-1900-is-leap-year).