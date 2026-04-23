# Edit Result Code Mappings

*Result codes* are informational values returned by verification services during address verification strategy processing. These codes can indicate that a location is valid, an address is not valid, a phone number has an invalid prefix, and other types of feedback. If you do not choose to map the result codes, you can view them when you view information on a data member processed by an address verification strategy. When result codes are mapped to attributes, they are retained for future use, and you can then filter members based on the codes and even run business rules to validate members with particular codes. The Address Verified code is commonly used as the criteria for members to be processed by a matching strategy.

On the Mailing, Name, Email and Phone tabs of an address verification strategy, you can optionally map results codes to attributes in an entity. Use the following procedure to map the codes:

1. Click **Edit Result Mappings**.

The Result Code Mapping window opens.

In the far left column of the Result Code Mappings screen, icons display to indicate the type of code:

- Successful match without edits
- A code in which an edit was executed on your data in order to return a result
- Informational code
- Warning code
2. Locate the codes for the information you want to map.
3. In the **Output Attribute** column, select the attribute that will hold the output information for each code, or click **Create New** and complete the process of creating a new attribute.
4. In the **Output Value** column, enter the value to be displayed when a member returns that code.

You may prefer to assign a value to a particular result code that is meaningful to your organization. For example, the code AS01 means that an address is verified; however, a custom value for a verified address may make more sense for your organization. If no output value is specified, then the default value is used.

5. In the **Priority** column, rank the importance of this code on a scale of 0 (most important) to 42 (least important). You can use the same ranking for multiple codes, and you can also use 0 for all of the codes if they are all equally important.

The Priority column determines the code used when the verification service returns multiple codes for a single record. The output value with the highest priority is used.
6. Click **OK**.

The result code mappings are applied to the strategy.