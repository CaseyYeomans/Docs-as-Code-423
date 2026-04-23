# Configuring the Output Attributes Tab

Select and create attributes manually, or use the AI-Assign function. These attributes store output values from the matching process. The strategy control attributes include the following:

* **Match Cluster ID**—A free-form text attribute that identifies the records of individual match groups and allows them to be sorted and filtered.
* **Match Score**—A free-form number attribute that identifies how likely a record is to be a match. The maximum score is 1.0.
* **Match Status**—A domain-based attribute which stores the matching status for each record in the matching process. If this attribute is created by the strategy, a domain entity named Match Status is created that is used as the domain for this attribute. You can also click the Add New field to [add a new domain-based attribute](https://support.profisee.com/wikis/profiseeplatform/creating_entities_and_attributes_in_profisee_portal) to be used as the Match Status.

  The Match Status attribute can have the following values:

  | **Record Code** | **Record Name** |
  | --- | --- |
  | 0 | No Status |
  | 10 | Golden Record |
  | 20 | AutoApproved |
  | 30 | Proposed |
  | 40 | Approved |
  | 50 | UserMapped |
  | 60 | Unique |
  | 70 | Rejected |
* **Record Source**—A domain-based attribute that designates the source system for each record. The domain entity for this attribute contains the record Profisee uses to identify the golden records, if created by the survivorship process.
* **Match record**—A recursive domain-based attribute that points to the record responsible for bringing the record into the group.
* **Strategy step**—A free-form text attribute identifying the strategy and attribute set that bought the record into the match group.
* **Match date**—A free-form date attribute indicating the date and time that the match cluster formed.
* **Match user**—A free-form text attribute identifying the account name for the user that last changed the match cluster status. This attribute is only populated for records matched incrementally.

It is recommended to populate all output attributes for matching and survivorship. Auto-Assigning is recommended for users with AI capabilities enabled. It is recommended to use one of the built-in prompts when using the AI Assign feature..![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i78ef66870bd8ec3c.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4d49985bcbf9ab6f.png)

---