# Reverse Transaction

The Reverse Transaction button allows a user with sufficient permissions to roll back a set of changes made to a record in Profisee FastApp Portal. To reverse changes to a record, you must have the permissions required to make changes to that record and all attributes included in the transaction.

As long as the transaction did not create or delete the record, and as long as no attributes of the record are Restricted, you can undo a full set of changes made to a record. This functionality can only reverse a full set of changes and cannot change portions of a change set.

1. Navigate to an entity grid containing a record that has a history of changes.
2. Select the record containing changes you want to reverse.
3. Click the **History** system tab on the record panel.
4. Hover over the transaction you want to reverse and click the Reverse Transaction button.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i343ed6da7813922c.png)

If there are unsaved changes on a form, you will receive a prompt before the transaction is reversed. If you choose to continue with the reversal, the changes will be lost.

If you reverse a transaction that includes a code change, the transaction reverses successfully, but the form closes and the record is not found.

Changes to that record are rolled back. When finished, a new transaction is created to indicate that a transaction has been reversed.