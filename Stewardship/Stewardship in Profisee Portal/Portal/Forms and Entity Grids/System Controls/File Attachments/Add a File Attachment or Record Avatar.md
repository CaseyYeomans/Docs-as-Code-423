# Add a File Attachment or Record Avatar

A user with Update permissions can add a file attachment to a record within the Profisee web portal. Users with Read-Only permissions can view and [download](https://support.profisee.com/wikis/profiseeplatform/download_or_delete_a_file_attachment) file attachments from the portal, but cannot add or [delete](https://support.profisee.com/wikis/profiseeplatform/download_or_delete_a_file_attachment) them.

Similarly, **Record Avatars**are read-only image files that can be used to add icons at the record level to represent the actual data value of a record. These avatars are displayed in the portal wherever the entity icon is displayed.

To upload a file attachment or record avatar:

1. Navigate to a field within the Profisee web portal that contains a record and has been [configured for file attachments.](https://support.profisee.com/wikis/profiseeplatform/configure_an_entity_for_file_attachments)
2. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3d777efdd7c87944.png)Right-click a record and select **Open**to open the record in form view**.**
3. Click the rightmost **View record files** tab in the form view.
4. Click **Upload an attachment.** ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i17c36d19f9e79bf4.png)
5. Click the dropdown menu under **Category** and select a file attachment or record avatar category.
6. Click **Choose a file**.
7. Select a file from your machine that matches one of the listed file extensions and click **Open.** If the allowed file extensions are designated as **(.\*)**, all file extensions are allowed.

If the uploaded file shares a name with a file that has already been attached, the new file will overwrite it.

Note that Record Avatars cannot exceed a file size of 1MB.

8. Click **Save.**
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iff70b9c8aff03598.png)

File attributes (such as Read-Only permissions) are not maintained when attached to a record. Use other security methods such as password protection to protect file contents.

If a record with a file attachment is [cloned](https://support.profisee.com/wikis/profiseeplatform/cloning_records), the file attachment is not carried over to the new record.