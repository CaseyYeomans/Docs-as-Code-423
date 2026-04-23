# Null Handling and Auto Add DBAs in Staging Table Definitions

### Apply Nulls

You can configure the treatment of nulls through the **Attributes** tab in **Administration | Staging Tables**. The column to the right of the attribute name allows you to select **Apply Nulls** for all applicable attributes. By default, all applicable attributes are unselected. This causes a null value in the attribute field to be ignored during staging if it appears in the specified column. An existing value in the target cell will not be changed when the table is processed.

To change the behavior and apply nulls to the associated member, click the **Apply Nulls** checkbox to the right of the attribute name. Nulls applied to the staging table will now overwrite (or clear) the existing values in your data. If data exists in a cell that is null in the staging table, the specified data will be used. However, if the staging table has a **null** value, then the target attribute in the associated member will be cleared when the table is processed.

If you want to apply nulls to all applicable attributes, check **Apply Nulls** to the right of Select All. If you want Apply Nulls to be checked by default for new attributes, check **Apply Nulls** underneath **Default Behaviors for New Attributes.**

### Add Domain Values

You can configure the treatment of domain values through the **Attributes** tab in **Administration | Staging Tables**. The column two fields to the right of the attribute name allows you to select **Add Domain Values** for all applicable attributes. By default, all applicable attributes are unselected. IfAdd Domain Values is unselected, domain attribute values that don't exist in the domain entity will be invalid. For instance, if the Color domain entity only has Blue and Red values, a product record with a Green color value will be invalid and not processed.

To change the behavior to the associated member, click the **Add Domain Values** checkbox two fields to the right of the attribute name. When selected, domain attribute values that don't exist in the entity will be created during staging. For instance, if the Color domain entity is selected and only has Blue and Red domain values, a product record with a Green color value will create a new Green domain value.

If you want to add domain values to all applicable attributes, check **Add Domain Values** two fields to the right of **Select All**. If you want **Add Domain Values** to be checked by default for new attributes, check **Add Domain Values** underneath **Default Behaviors for New Attributes.**

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i2fc0e0c1511a3eff.png)

## See Also

[Staging Tables Overview](https://support.profisee.com/wikis/profiseeplatform/staging_tables_overview)

[Managing Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio)