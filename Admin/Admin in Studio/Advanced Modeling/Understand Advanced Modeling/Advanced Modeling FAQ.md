# Advanced Modeling FAQ

The following are answers to frequently asked questions about Matching and Survivorship administration:

- Why do I receive an error stating that the 'keygenlast value may be incorrect for this entity'?

Attempting to add new members to a entity grid may result in this error.

In this example instance, the values for KeyGenLast and KeyGenSeed are out of sync. Where the KeyGenSeed = 1000, KeyGenLast = 1239, and the entity already has 260 existing members, set the KeyGenLast value to a number greater than 260 to resolve this issue. Under normal circumstances, both numbers should stay in sync. However, manual intervention is sometimes required. Users will need database access in order to make the required changes.

- Why does my model import fail when I use the CLU, but succeed through the UI?

When you publish through the UI, there are 2 options that appear: Merge or Replace.

Merge is the default action, and it will only 'add' or 'update' (but will not 'delete'). When you publish using the CLU, no option is given, and it will 'replace' automatically. If anything would be deleted using a 'replace,' the CLU import will fail. Similarly, if there is a conflict (conflicts are also shown in UI during merge) you cannot publish using the CLU and you must use the UI and resolve the conflict.

The CLU can only be used when there are no conflicts (this means metadata matches by name & guid) and there are no deletes.

- I added an attribute to my model, but I am presented with many conflicts that I thought I had already resolved last time I published. Why?

When you resolve conflicts during publishing, you only resolve them for that publishing instance. To avoid this on the next publish, after your model changes are published, open the model from the server and save as file. Publishing from this file will avoid these conflicts.