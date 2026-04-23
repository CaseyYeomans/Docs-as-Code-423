# Best Practices for Using Synonym Lists

- When a strategy contains the same attribute in multiple attribute sets, select the same synonym list for that attribute for all attribute sets. Only one synonym list is allowed per attribute in a strategy. If you attempt to select multiple synonym lists for the same attribute in different sets, the first one is selected automatically for all attribute sets.
- Arrange synonyms within the list in a logical way so that synonym processing proceeds correctly. Remember that synonym replacement occurs sequentially.

For example, if you want to both replace "St." with a blank, and all periods with blanks, be sure to place the period replacement after the "St." replacement. The "St." replacement will never find a matching string if the period replacement occurs first and removes the period from the abbreviation.
- Replace longer strings with shorter strings when those values are less significant:

For example, change "Street" to "St" in addresses.
- Replace shorter strings with longer strings when those values are significant:

For example, "Bob" to "Robert" in names.
- Remove words altogether that are optional because they are just noise to the matching process.
- For company names, remove all terms (replace with blank) like "company," "co," and "inc." It is just as likely for someone to enter "Microsoft" as they would "Microsoft Corporation."
- Copy and paste functionality is enabled in the synonym list maintenance grid. Use this to build and maintain lists of synonyms outside of Profisee in Excel, and copy those lists into Profisee.
- Make sure the Search in String option is selected for appropriate synonyms. For example, if you want to replace "inc" in company names, leave the Search in String option cleared. In this way, Profisee will replace the "inc" in "ABC Company Inc" but will not replace the "inc" string in "Vincent Smith Corporation."
- Select the Search in String option wherever one word replaces multiple words.
- Use synonyms together with the "exclude members" option for handling blanks in strategies to eliminate members with known inappropriate values from matching. These values could include placeholder values or system-generated values to represent missing information. For example, SSN = 000000000 in your data may indicate a member that does not have Social Security number information available for it. If thousands of members exist in your data with this SSN value, it is unlikely that you will want to create a single, large match group containing all of them. Instead, use the synonym lists to replace the placeholder value with a blank, and use the exclude members option for handling blank values for that attribute.

## See Also

[Use Synonym Lists](https://support.profisee.com/wikis/profiseeplatform/use_synonym_lists)

[Create a Synonym List](https://support.profisee.com/wikis/profiseeplatform/create_a_synonym_list)