# Use Synonym Lists

The Profisee matching process uses Synonym lists to replace words or abbreviations with standard terms to improve matching results. During synonym substitution, the input record strings are updated with synonym replacements on their way into the matching process to improve the matching process results. The data records in Profisee are never permanently altered (for example, "100 Main St." is replaced with "100 Main Street" before the matching algorithm is applied). All strings are converted to lower case, so capitalization is not important.

During the matching process, the size of the resulting string matters because the matching algorithm works on similarity. The larger the number of characters that are shared between strings, the higher their match score will be.

Follow these general guidelines for using Synonym Lists:

- Replace longer strings with shorter strings when those values are less significant:

For example, change "Street" to "St" in addresses.
- Replace shorter strings with longer strings when those values are significant:

For example, change "Bob" to "Robert" in names.

## Remove Unnecessary Words from the Matching Process

Use synonyms to remove words that are insignificant to the matching process. For example, when matching on company names, you could remove all terms (replacing them with blanks) such as "company," "co," and "inc." These words are unnecessary to matching because "Microsoft" is as likely to appear in data as "Microsoft Corporation." Removing these unnecessary terms can improve the matching results by removing irrelevant characters from the compared strings. Similarly, selecting **Remove repeating words** (as in "Morgan, Morgan, and Morgan") prevents repeating words from inappropriately requiring similar repetition in other members in order to form a match.

## Replace Words and Strings

Synonym replacement can be set to replace words or to replace strings. Typically, synonyms are used for replacing words in attribute values. For example, a synonym replacement for "co" acts on the third word in "Jerry's Motor Co" but not on the partial word in "Jerry's Motor Company."

Finding strings to replace relies on finding substrings within an entire field. The synonym "Motor Co" must be compared to the entire field value "Jerry's Motor Co". Therefore, any string synonyms are compared to the entire field contents. This also means that partial words may be found and replaced as in "Jerry's Motor Company."

To replace two words in a string with one word, you must select the Search in String option for that string. For example, you must select **Search in String** to configure the list to replace "San Francisco" with "SF".

## Replace Special Characters

The matching process ignores certain special characters. The following characters appear in the default Profisee synonym list and are replaced by an empty space during matching:

- -
- ,
- &
- and
- " "
- +
- @
- !
- #
- ^
- \*
- ~
- `
- (
- )
- '
- .

Synonym lists can be shared by multiple strategies.

## See Also

[Create a Synonym List](https://support.profisee.com/wikis/profiseeplatform/create_a_synonym_list)

[Best Practices for Using Synonym Lists](https://support.profisee.com/wikis/profiseeplatform/best_practices_for_using_synonym_lists)