# Configuring the Survivorship Options Tab

1. Select the checkbox for **Create and update golden records for unique records** if desired. This option lets you treat unique records and records in match groups consistently, as every source record has a golden record. Golden records for unique records appear in the list of Match Groups with only one record (the unique record).
2. Select the checkbox for **Only update clusters that have changed since last run** if desired. This option allows you to apply survivorship only to groups where one or more control attributes, survivorship attributes, or attributes used in the promotion criteria have changed since the last processed transaction. Applies to batch processing only. Changes to multi-level attributes are not detected.
3. Select the **Golden Record Prefix**. This is the character string that will prefix each golden record. Use the default "GoldenRec-" value, or specify a different prefix up to 10 characters. This prefix is used to create a unique code for golden records.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i693fcabdf810ec9a.png)

---