# Strategy Tab

Matching and survivorship strategies define the settings and context for the matching and survivorship processes. Strategies are specific to a model, version and entity, and are configured to match based on a subset of entity attributes.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i832f03cea75a7c17.png)

Note that you cannot select matching attributes that have more than 450 characters.

## Basic Strategy Information

1. In the navigation panel, click **Administration**.
2. Click **Matching and Survivorship**.
3. On the matching toolbar, click **New**.
4. On the Strategy tab, enter the following:

- **Name**--A unique name for the strategy
- **Entity**--The entity containing the source records to be matched

Only the entities where the user has Administration permission display in the list.

## Strategy Components

5. Select the options to include in this strategy.

- **Matching**--Create match groups based on the settings defined on the Matching tab.
- **Survivorship**--Create golden records for match groups and survive attribute values from representative match group records as defined by settings on the Survivorship tab.

## Control Attributes

6. Select and create attributes manually, or use the Attribute Assistant. These attributes store output values from the matching process. Choose Select existing attributes to use only existing attributes, or choose Select existing and create new to use existing attributes where possible and to create new attributes that are not yet present in the entity.

The strategy control attributes include the following:

- **Match Cluster ID**--A free-form text attribute that identifies the records of individual match groups and allows them to be sorted and filtered.
- **Model Confidence**--A free-form number attribute that identifies the match score for a record.
- **Match Member**--A domain-based attribute which stores the matching status for each record in the matching process. If this attribute is created by the strategy, a domain entity named Match Status is created that is used as the domain for this attribute.

The Match Status attribute can have the following values:

| Record Code | Record Name |
| --- | --- |
| 0 | No Status |
| 10 | Golden Record |
| 20 | AutoApproved |
| 30 | Proposed |
| 40 | Approved |
| 50 | UserMapped |
| 60 | Unique |
| 70 | Rejected |

- **Record Source**--A domain-based attribute that designates the source system for each record. The domain entity for this attribute contains the record Profisee uses to identify the golden records, if created by the survivorship process.
- **Match record**--A recursive domain-based attribute that points to the record responsible for bringing the record into the group.
- **Strategy step**--A free-form text attribute identifying the strategy and attribute set that bought the record into the match group.
- **Match date**--A free-form date attribute indicating the date and time that the match group formed.
- **Match user**--A free-form text attribute identifying the account name for the user that last changed the match group status. This attribute is only populated for records matched incrementally in the Matching Results tab.

After you complete settings on the Strategy tab, you can continue to the Matching or Survivorship tabs to specify the attributes to be used in the matching and survivorship processes.

It is recommended that you create the Match Status attribute from the strategy so that the entity is correctly populated with the match status record values.

Typically, the Record Source attribute exists prior to creating the matching strategy in order to identify the records loaded into Profisee. It is also commonly called Source System. Select this attribute manually if you want to use existing entity data.

The control attributes are created as restricted attributes with Clear on clone enabled.