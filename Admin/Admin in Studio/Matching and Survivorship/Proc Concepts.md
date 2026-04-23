# Processing Concepts

There are multiple ways to run the processes configured in the matching strategy. The recommended ways are outlined below:

| | | | |
| --- | --- | --- | --- |
| Process | On Demand | Continuous | REST API |
| Clear by Criteria | Yes | No | Yes |
| Clear All Results | Yes | No | Yes |
| Match Only | Yes | Yes | Yes |
| Survive Only | Yes | No | Yes |
| Match + Survive | Yes | Yes | Yes |
| Interactive | No | No | Yes |

\*Workflow actions can also trigger processing. For more details, see Worklow feature.

### On Demand:

#### Process Clearing

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id7a06acf7b3858b2.png)

You can selectively clear existing matching results using the **Clear** button on the matching toolbar within the Matching and Survivorship administration tab. Clearing sets the Output Attributes defined in the strategy to blank. You can clear results on matching strategies regardless of whether they are enabled or disabled.

Creating a separate strategy to clear records is recommended. Add a name that clearly shows that the strategy should be used for clearing only, not matching or survivorship. Make sure you set the Clearing filter to Matching From criteria section and set the status to Disabled.

After clearing using either option below, golden records that no longer have child records are deleted. Special records are deleted if not linked to any children.

The Clear Prior Results window displays the following options:

- **Clear prior matching results (match groups, scores, statuses) for this strategy -**This option clears matching results for records that meet the *Matching-From* criteria used for the strategy. This option can only be effectively used on strategies that have been previously run with a filter.

####

- **Clear all prior matching results** - This option clears matching results for all records on this strategy.

####

#### Process Matching and Survivorship

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9b7be99e4715ee9a.png)

To run Matching and/or Survivorship On Demand

1. Click **Administration** in the navigation panel.
2. Select **Matching and Survivorship**.
3. Select the strategy to process.
4. Click the Run button.
5. Select **Matching**options, and if desired, select **Survivorship** options.

- Index - Index and score records based on the set attribute configuration.
- Cluster - Clusters records based on set attribute configuration. Clustering requires Indexing to be selected.
- Include Promotion - Create golden records and populate golden record attributes from source record attributes.
- Include Harmonization - Populate source record attributes from golden record attributes.

6. Click **Start**.

You can run any combination of matching and survivorship that is valid for your strategy.

- Matching Only

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3574fac9fc7c934c.png)

- Survivorship Only

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i56b5dcba6553eeb3.png)

- Matching and Survivorship

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibb9f089c277ecd77.png)

### Continuous Options

You can set up the Matching & Survivorship to process all new and changed records continuously, without having to trigger the strategy. The system continuously monitors all incoming transactions like Create, Update, Delete and automatically Indexes, Matches and Survives the records based on the Processing options. When Continuous mode is ON you do not need to run the strategy On Demand.

To turn Continuous Mode ON:

1. Click **Administration** in the navigation panel.
2. Select **Matching and Survivorship**.
3. Select the strategy to configure.
4. Click the **Edit** button.
5. Select **Processing Options**, and choose **Enabled**. Optionally choose one of the following options:

- Automatically identify clusters for unclustered records
- Automatically perform survivorship as data is created, updated, and deleted

6. Click **Save and Close**.

#### Options:

- Auto-Index only

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i101686e151a5064b.png)

- Auto Index + Auto-Match

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i12d5bc07ed2de38c.png)

- Auto-Index + Auto Match + Auto Survive

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7355cbdcc58c9380.png)

### REST API

All processing options can be automated using the Profisee REST API. You can edit and trigger matching strategies, as well as perform actions on individual records like Lookup, Match and Unmatch. For full details on each available APIs:

1. Navigate to the REST API Swagger URL at https://servername/profisee/rest/docs/index.htm
2. Expand the desired section and click on the API to see a description.
3. Click **Try it out** and enter the required information.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ica33ae142dca2992.png)

###

### Multiple Strategies

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib93f0d1ae67bf3d5.png)On Demand

Multiple strategies can be triggered On Demand at the same time, but consideration should be made for the sharing of available resources. Each strategy is configured to run multiple jobs, and each job is multithreaded. When triggering more than one strategy at a time, monitor your hardware resources to make sure you are not overloading the system.

Continuous

Multiple strategies can run in Continuous mode at the same time, but consideration should be made for the sharing of available resources. Each strategy is configured to run multiple jobs, and each job is multithreaded. When enabling more than one strategy at a time, monitor your hardware resources to make sure you are not overloading the system.

When multiple strategies that share the same output attributes on the same entity are running in Continuous Mode, they will process incoming transactions in alphabetical order by Strategy Name ascending. For example:

1. Transaction 1 for 3 new records comes in.
2. Strategy A picks up Transaction 1.
3. Strategy B picks up Transaction 1 once Strategy A has completed processing it.

### Incremental Matching

Running a matching strategy places similar records together into groups, creates representative golden records (when survivorship is defined), and identifies unique records. A data steward then reviews the match groups, approving or rejecting proposed matches, placing unique records into groups, and potentially populating the golden records with more complete data.

Incremental matching preserves the approved groups, as well as any work performed by the data steward. All unmatched records are compared to records in the matching index, and matched accordingly to existing groups.

Groups already created during previous matching runs are preserved during incremental matching. New, unmatched records are matched with records in existing groups (both unique records and matched records), and with each other. Groups that are present in matching results will never split to form multiple groups, unless matching results are cleared.

### Incremental Survivorship

Processing a strategy with survivorship reapplies survivorship rules to all records of all match groups by default. This can take a long time to complete for large record volumes. To make a strategy more efficient for incremental runs, select the **Only update groups that have changed since the last run** option on the strategy Options tab, under the Survivorship tab. For more information, see [Survivorship Concepts](https://support.profisee.com/wikis/profiseeplatform/survivorship_concepts). By selecting **Only update groups that have changed since the last run**, Profisee will not process groups that have not changed since the end of the last successful process of the strategy. If a group has been changed for any reason, such as a data change in an existing group record or a new record joining the group, then data values may need to be re-promoted or re-harmonized; therefore, the group will be reprocessed by survivorship.