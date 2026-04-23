# Configuring the Stewardship Tab

The Web Stewardship tab defines the matching and survivorship options available to data stewards.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ifdaa14dd326c0d25.png)

#### Stewardship Configuration

Click the appropriate checkbox to enable each of the following options:

* Approve or reject a record in the cluster

#### Survivorship

* Apply survivorship to the cluster
* Allow manual promotion to Golden Record

  + Allow Promote All
* Allow manual harmonization to source records

  + Allow Harmonize All
* Allow Merge
* View match details for a record

Select an appropriate option from the dropdown lists for the following options:

* Orphaned golden record behavior (Retain or Delete)

An orphaned record is a golden record that has no children records in the match cluster. This situation can occur if a steward reviews matching results and manually splits or combines records from at least two match clusters where a golden record is left alone without any other records in its match cluster.  
  
It can also occur if a golden record's match cluster records are deleted from the source systems and are removed from the data set. If the above **Orphaned golden record behavior** setting is set to Delete, Profisee automatically deletes orphaned golden records.

* Stewardship View (Select a Presentation View)

The presentation view displays unrestricted attributes for this entity under the Survivorship section of the portal. Attributes displayed here can be used to change the values on match records if Promotion and Harmonization are enabled.   
  
Control attributes should not be manually set using Promotion or Harmonization; they should be Restricted as not to be displayed in the presentation view.

* Open / Edit Form (See [Forms](https://support.profisee.com/wikis/profiseeplatform/forms_administration_in_profisee_portal) for more information)

---