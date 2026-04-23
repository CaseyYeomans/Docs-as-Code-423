# View Similarity in FastApps Portal

Once an entity grid has been [configured for matching in Profisee FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/configure_the_entity_grid_control), you can view the similarity between two matched records in the web portal.

1. Click the **Match Cluster ID** of the record you want to view.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i810557f408370d29.png)
2. Click the match score to view the match details for this record.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8817ac3a173e2db3.png)
3. Click the similarity score of a matching attribute to view the similarity calculations.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i34faf60aa64e7f22.png)

By default, the value for the selected attribute is compared to the value for the match record. The following information displays:

- **Text A**--The matching attribute value from the matching record. This record brought your selected record from the grid into the match cluster.
- **Text B**--The matching attribute value from the selected record (when opened from the Match Details dialog) or the match record (when opened from the bottom grid in the Matching Results tab).
- **A Tokens**--These are the tokens created from Normalized Text A that were used in matching. Normalized values are the text values after synonyms are applied. Strings that are compared may be of three match types: token, word, and exact. The match type is defined in the matching strategy.
- **B Tokens**--These are the tokens created from Normalized Text B that were used in matching. Normalized values are the text values after synonyms are applied. Strings that are compared may be of three match types: token, word, and exact. The match type is defined in the matching strategy.
- **Common Tokens**--The tokens the two strings have in common. This list is created from the overlap of A Tokens with B Tokens.
- **Similarity**--The result of the similarity calculation (at the bottom of the dialog). The counts of Common Tokens, A Tokens, and B Tokens are entered into the formula and the result displays as the Similarity.

The Match Type and (if applicable) Token Type selected in the strategy are also applied in the Similarity Calculation.

You can type other string values into the Text A and Text B fields, and then click Recalculate to see how they compare using the settings for matching. This feedback can be useful when you are starting to create matching strategies and want to see how your settings affect match results.