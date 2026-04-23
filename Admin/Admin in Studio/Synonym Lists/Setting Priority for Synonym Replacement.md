# Setting Priority for Synonym Replacement

The synonym replacements are applied in the priority order specified. You can control the order by moving the synonym or term definitions up or down in the list as described below.

1. Select **Administration** in the navigation panel.
2. Select the **Synonym Lists** administration task.
3. Highlight the synonym list and click **Edit**.
4. Select a row and click either the Up or Down arrow buttons in order to move the member in the list to change the priority order.
5. Click **Save**.

The order of synonym replacement rules can be important if rules interact with each other. For example, if there is a rule to replace "St." with a blank, and a rule to replace periods with blanks, then the rule replacing "St." must appear before the rule replacing periods. If the rule replacing periods appears first, then there will be no "St." matches, because all of the "St." strings will have been replaced by "St " (the letters S and T followed by a space). The rule replacing "St." would therefore not produce the intended results.

## See Also

[Use Synonym Lists](https://support.profisee.com/wikis/profiseeplatform/use_synonym_lists)

[Create a Synonym List](https://support.profisee.com/wikis/profiseeplatform/create_a_synonym_list)