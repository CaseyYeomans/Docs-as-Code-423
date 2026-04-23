# Data Products Overview

A Data Product is a collection of entities that can be organized to more easily manage Profisee instances with a large amount of data. You can think of a Data Product as a filter by which different entities are grouped into a single cluster that can be managed and edited all at once. Once a Data Product is defined, you can work with and export only the portion of the model that relates to the currently selected data product, allowing for more convenient administration. You can also use Data Products to filter Connect Strategies to show only those associated with each Data Product, then export them individually.

For example: A user creates two Data Products labeled **Company** and **Customer**in an instance with two entities labeled **Product** and **Currency**. That user could associate the **Currency** entity with both Data Products, but could associate the **Product** entity with only the **Company** Data Products.

| | | |
| --- | --- | --- |
| | Product Entity | Currency Entity |
| Company Data Product | **Yes** | **Yes** |
| Customer Data Product | **X** | **Yes** |

Data Products can be selected from the **All Data Products** field in the top-left corner of the Administration area in Profisee Portal. You can also create a new data product by clicking **Add new** at the bottom of the list of available Data Products.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ifb6318578d5edce8.png)

*Note that as of 2024.R2, the only administration area affected by data products are Integration Strategies. More areas will have this functionality in future releases.*