# View Match Details

After you have opened the Matches dialog using the procedure in [View other possible matches](https://support.profisee.com/wikis/profiseeplatform/view_other_possible_matches_for_a_member), you can see the details of the matching attributes for two records by using **View match details**. Viewing the match details can help you understand why match groups formed the way they did.

To view match details:

1. Do one of the following:

**--or--**

- From the Matches dialog, right-click a record in the list to compare it to the highlighted record.
- From the bottom grid of the Matching Results tab, right-click a match group record.
2. Click **View Match Details** on the menu

The Match Details dialog appears

Matching must be enabled on a strategy to view match details. If matching is not enabled on the strategy, an error will return.

3. Compare the two records displayed in the grid.

By default, all attributes for both records display. You can limit the attributes shown by selecting an attribute group tab. The rows for the attributes used in matching are highlighted.

The similarity for the two records displays for each matching attribute. If the similarity score is below the matching threshold for an attribute, **< [*match threshold value*]** displays.

The graphic at the bottom of the dialog illustrates the location of the similarity score ranges for auto-approved matches (green), proposed matches (yellow), or not considered matches at all (gray).
4. To view the actual similarity calculation for any pair of attribute values, right-click the attribute value and then select **View Similarity Calculation** on the menu.

The Similarity Calculation Details dialog appears.
5. Compare the strings for the two records. For more information, see [Use the Similarity Calculation Details dialog](https://support.profisee.com/wikis/profiseeplatform/use_similarity_calculation_details).
6. When you finish viewing the information on matches, close the open dialogs and return to the Matches dialog.