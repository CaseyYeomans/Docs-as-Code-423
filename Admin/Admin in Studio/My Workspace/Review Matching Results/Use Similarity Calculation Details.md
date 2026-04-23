# Use Similarity Calculation Details

The calculation displayed in the dialog helps you understand the similarity of two matching attribute values. This is helpful when you want to understand why matches did or did not form.

The formula used for matching similarity calculations is: *Similarity = ((Common Tokens) ^ 2 / (A Tokens) \* (B Tokens)) ^ 0.5*.

You can access the Similarity Calculation Details option in two ways:

- By right-clicking a matching attribute value in a match group member in the bottom pane of the Matching Results tab.
- By right-clicking a matching attribute value (shaded in gold) in the Match Details dialog. For more information, see [View match details](https://support.profisee.com/wikis/profiseeplatform/view_match_details).

By default, the value for the selected attribute is compared to the value for the match member. The following information displays:

- **Text A**--The matching attribute value from the matching member. This member brought your selected member from the grid into the match group.
- **Text B**--The matching attribute value from the selected member (when opened from the Match Details dialog) or the match member (when opened from the bottom grid in the Matching Results tab).
- **A Tokens**--These are the tokens created from Text A that were used in matching. Strings that are compared may be of three match types: token, word, and exact. The match type is defined in the matching strategy.
- **B Tokens**--These are the tokens created from Text B that were used in matching. Strings that are compared may be of three match types: token, word, and exact. The match type is defined in the matching strategy.
- **Common Tokens**--The tokens the two strings have in common. This list is created from the overlap of A Tokens with B Tokens.
- **Similarity**--The result of the similarity calculation (at the bottom of the dialog). The counts of Common Tokens, A Tokens, and B Tokens are entered into the formula and the result displays as the Similarity.

The Match Type and, if applicable, Token Type selected in the strategy are also applied in the Similarity Calculation.

You can type other string values into the Text A and Text B fields, and then click Recalculate to see how they compare using the settings for the matching. This feedback can be useful when you are starting to create matching strategies and want to see how your settings affect match results.