# Managing Strategies

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5c308da4015425fc.png)

To access the matching and survivorship strategy options, click **Matching and Survivorship** under the Administration area of the navigation panel. The following options are available on the Matching and Survivorship toolbar:

- **Adding a new strategy**: Click **New**to add a new strategy.
- **Duplicating a strategy**: Select a strategy, and then click **Copy**to create a duplicate copy. Note that you must change the name of the strategy so that it is unique.
- **Deleting a strategy**: Select a strategy, and then click **Delete** to remove it.
- **Importing a strategy**: Click **Import/Export** and then select **Import** on the menu. Select one or multiple strategy files to import, and then click **Open**.
- **Exporting a strategy**: Select one or multiple strategies in the list. Click **Import/Export** and then select **Export** on the menu. Browse for the location where you want to save the strategy, and then click **Save**.

When you import a matching strategy, Profisee attempts to map the attributes to existing attributes in the new environment. If appropriate attributes cannot be found, Profisee flags the attribute with a red exclamation mark. This symbol means that you must remap the attribute manually.

#### Multi-Level Strategies

When the customer needs to group the records in an entity on more than one level. An example of this is the Individual and Household strategies.

To configure this scenario, the Individual strategy should be configured for Matching and Survivorship, so Individual duplicate records are grouped together in a cluster, and each Individual cluster gets a Golden Record to represent it. The Individual strategy should have its own set of Output Attributes, and the Golden records from the Household Strategy should be filtered out of it.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2d1efee5c717d7d6.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5606c156fa44c01f.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i547c99433e78aca.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i977d718eeefbc79d.png)

The Household strategy should have a separate set of Output attributes, and the From and To filters should be set to the Individual Golden records. This way, all the Individual Golden Records are grouped together into Household clusters. Optionally, a golden record for the Household cluster can be created with a separate Golden Record prefix.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia341710d8bd6ade2.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ied1dbac7d370326a.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib22c033e39c1f74e.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id8ddb0e2783a20b0.png)

#### Lookup-Only Strategy

When the customer requires different criteria to be used for Lookup then for Matching, a Lookup-Only strategy is recommended. For example: The minimum criteria for matching is both Name and EmailAddress must match, but the customer wants to be able to Lookup by Name only or EmailAddress only. A separate strategy can be created for Lookup-Only, where Matching sets are configured with less attributes. This strategy will share the same Output Attributes as the Matching strategy, but will only be processing Auto-Indexing, and not Matching or Survivorship.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib07fd461560ec98c.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iccb5bbc0fca69b54.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9f8b4d3f89e495e2.png)

To be sure that no new/unmatched records will accidentally be matched by the Lookup-Only Strategy, you can use a filter to eliminate all unmatched records.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ieb366e18a295cbfe.png)

#### Clearing-Only Strategy

When the customer requires different criteria to be used for Clearing then for Matching, a Clearing-Only strategy is recommended. For example: The criteria for matching is Name and EmailAddress, but the customer wants to clear all records from a specific source system, like Salesforce, and reprocess them. A separate strategy can be created for Clearing-Only, where the Matching From criteria is used for clearing. This strategy will share the same Output Attributes as the Matching strategy, but should stay Disabled to make sure it is not used for Matching or Survivorship.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2cfa830f03364d67.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2ecfa42bb7286fb6.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibf72019a7f2dfb10.png)