# Matching and Survivorship Overview

Matching and survivorship solves the problem of duplicate records that represent the same thing. The matching process clusters together multiple records identifying the same customer, product, or other object described by golden record data. Survivorship creates golden records containing the best data to represent those clusters.

Profisee provides matching and data survivorship abilities to:

- Identify duplicate records
- Cluster similar records together in easily identifiable clusters
- Review and modify resulting match clusters
- Create representative golden records for clusters
- Enhance source records with harmonization

## Preparation for Matching and Survivorship

To prepare the Profisee model for the matching process, load your source records into a single entity and create a domain-based attribute to indicate the source of each record. You can then create a matching strategy in Profisee, specifying matching criteria and creating other control attributes that implement and monitor the matching process.

The result of this matching process can then be published to Profisee, where golden records may optionally be created in the same entity.

The cluster records are mapped together by the same Cluster ID, along with the associated match scores and match status for each source record. If survivorship is defined, cluster records are also mapped to the golden record using the golden record recursive attribute defined in the matching strategy.

## Matching

The matching process evaluates records within a single entity, clustering together similar records based on the matching criteria defined in the matching strategy. Matching assigns the similar records an identifying cluster code.

One or more attribute sets define the values that are compared during the matching process. The matching algorithm then finds the best possible matches. Profisee categorizes the matches as either automatically approved or proposed (in need of review), based on the thresholds defined in your matching strategy.

### Matching Thresholds

There are two thresholds that are used to drive the matching process:

- **Auto-approve Threshold**
- **Match Threshold**

For more information, see [Matching thresholds](https://support.profisee.com/wikis/profiseeplatform/matching_concepts).

Records with match scores that fall between the match threshold and the auto-approve threshold for all attribute sets are proposed matches that can then be reviewed and approved or rejected by data stewards. Those records that are not matched to any other record by any attribute set are unique.

### Match Clusters

Matching results are published to control attributes in Profisee as defined in the matching strategy. The Cluster ID attribute identifies records belonging to the same match clusters. Other control attributes, such as Match Status and Match Score, indicate the quality of the match.

### Synonym Substitution

Synonym substitution can often improve the quality of matching results by increasing the match scores of data records that are similar. In synonym substitution, the input record strings are updated with synonym replacements on their way into the matching index. The source record data is never permanently altered. For example, "Acme Incorporated" is replaced with "Acme Inc" or even "Acme" before it is processed by the matching algorithm. You can view the normalized versions of attribute values either by hovering your mouse over records in the Matches dialog or by viewing the similarity calculation. For more information, see [Synonym Substitution](https://support.profisee.com/wikis/profiseeplatform/synonym_substitution), [View other possible matches](https://support.profisee.com/wikis/profiseeplatform/view_other_possible_matches_for_a_member) and [Use Similarity Calculation Details](https://support.profisee.com/wikis/profiseeplatform/use_similarity_calculation_details).

## Survivorship

Survivorship includes both promotion and harmonization. Promotion defines how golden record attributes are populated from the source records in a match cluster, while harmonization defines how source record attribute values are updated from the golden record in the same cluster.

### Promotion

Promotion creates a golden record to represent each match cluster. The golden record can be selectively populated with data from representative cluster record records. Promotion is part of survivorship, and is configured on the Survivorship tab of the matching strategy.

### Harmonization

The goal of harmonization is to selectively update source record attribute values based on better data from the golden record. The primary purpose of harmonization is to signal when an update to a source system should occur, allowing source systems to make use of better data. Harmonization is probably not useful to organizations where there is no plan to propagate data to source systems.

To define the promotion and harmonization actions, create survivorship attribute sets in the strategy to specify the attributes to update, along with the criteria for updating the golden record or source records.

### Academy Preview

The following content is from the Profisee Academy course on Matching. Academy customers can see the full course [here](https://support.profisee.com/lms/courseinfo?id=00u00000000004n00aM).