# Matching Administration in Fabric

Profisee users can perform Matching Administration functions directly within Microsoft Fabric using the Profisee integration. Using the **Matching Strategies** section (accessible via the **Explorer** panel), you can create, configure, and manage matching strategies without leaving your Fabric workspace. This enables you to define matching rules to detect duplicates, configure survivorship logic to generate golden records, and manage your entire matching workflow through a Fabric-native interface.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icdbd7a1f8226e77b.png)

To access Matching Strategies, log into Fabric, select a workspace containing a Profisee Data Product, open the data product, and choose **Matching Strategies** from the **Explorer** panel on the left. The **Matching Strategies** grid is displayed with the following columns:

* **Name**: The name given to the strategy. Each name is also a hyperlink — clicking it opens the Strategy Configuration Form directly.
* **Entity**: The entity the matching strategy applies to.
* **Status**: Whether the strategy is *Enabled* or *Disabled*.

---

## Grid-Level Actions

The ribbon above the grid provides the following actions for managing your matching strategies:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i928c8f551cade610.png)

* **New / Add (+)**: Opens the **Add New Matching Strategy** drawer from the right side of the screen, allowing you to create a new strategy.
* **Edit** (pencil icon): Opens the selected strategy for editing.
* **Filter** (hamburger menu icon): Filters the strategies list.
* **Refresh** (refresh icon): Refreshes the grid to display current data.
* **Ellipses** (vertical ellipses): Reveals additional options for the selected strategies.

---

## Row-Level Actions

Select the ellipsis icon on any matching strategy (or right-click a row) to access context-level actions for an individual strategy. The available options depend on the number of selected rows and the strategy's current status:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if27fa7f870e2172e.png)

* **Open**: Opens the Strategy Configuration Form. Available only when a single row is selected.
* **Clone**: Makes a copy of the strategy, appends the word "Copy" to the name, and opens it in the Strategy Configuration Form. Available only when a single row is selected.
* **Enable**: Changes the status of the selected strategies to *Enabled*. Hidden if a single selected strategy is already Enabled.
* **Disable Rule**: Changes the status of the selected strategies to *Disabled*. Hidden if a single selected strategy is already Disabled.
* **Run**: Runs the selected strategy. Available only when a single row is selected and the strategy status is *Enabled*.
* **Clear**: Runs the strategy in clearing mode only. Available only when a single row is selected.
* **Delete**: Permanently deletes all selected strategies.

---

## Creating a Matching Strategy

To create a new matching strategy, click the **+** (New/Add) button in the ribbon. A drawer titled **Add New Matching Strategy** opens from the right side of the screen.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia2181c4353004d80.png)

You are presented with the following required fields:

* **Name \***: A text field for entering the strategy name. This field is required.
* **Entity \***: A searchable dropdown for selecting the entity you want to run the matching strategy against. This field is required.

Once both fields are completed, the **Continue** button becomes active. Select **Continue** to proceed to the **Matching Sets and Attributes** configuration tab, or select **Close** to exit the drawer without saving.

> [!NOTE]
> The Continue button remains greyed out until both the Name and Entity fields have been filled in.

---

## Configuring a Matching Strategy

From here, you can configure a matching strategy to specify the way the strategy functions. A strategy must be configured before it can have any impact on your data. This process mirrors the configuration process for matching strategies in Profisee Portal. Click [here](https://support.profisee.com/wikis/profiseeplatform/configuring_the_strategy_tab) for information on configuring a matching strategy.

Note the following about configuring matching strategies in Fabric:

* Matching and Survivorship are always enabled by default.
* You cannot create your own control attributes, but they are created for you.
* You can only configure settings on the Strategy, Matching, and Survivorship tabs. The other tabs (that can be configured in Profisee portal) have a set of default values in Fabric.

---

## 