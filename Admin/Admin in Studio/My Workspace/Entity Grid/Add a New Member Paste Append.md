# Add a New Member Using Paste Append

Use Paste Append for pasting new or updated members in the current entity grid. Paste data from any source that stores data in a tabular format.

## Adding members from an external source using paste append

1. Select the data in the source and copy it to the clipboard.
2. Do one of the following:
- If the source attribute columns are in the same order as the destination attributes in Profisee, click **Paste Append** on the menu.
- **--or--**
- If the source attribute columns are not in the same order as the destination attributes in Profisee, click **Paste Append With Headers** on the menu.

New members appear at the bottom of the current grid view, below all existing members.

## Add Members in FastApps Studio using Paste Append

Copy a member within Profisee and use Paste Append to duplicate it for use as a template.

1. Select the member to use as a template by clicking the row heading.
2. Copy the member to the clipboard.
3. In the entity grid, right-click and click **Paste Append** on the menu.

The new member appears at the bottom of the current grid view, below all existing members.

4. Change the member code to a new code. If you do not change the code, a new member will not be created.

Instead, the existing member will be updated with any changed values.

When data is published after members are copied and pasted using paste append, members with the same code are merged. Attribute values in the original member are updated to match the values in the appended member, and the duplicate member no longer exists.