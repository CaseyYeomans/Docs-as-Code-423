# Accounts and Teams FAQ

The following are answers to frequently asked questions about Matching and Survivorship administration:

- Can I change which attributes user can see based on a filter value?

No.

- Why can I see users if I only have group level permissions assigned?

Once a user connects, that user is added without any permissions (group permissions are determined when the user logs in).

- If I remove a user from a group, when will that change be applied?

The change will be applied when the user cache interval timer elapses. This system setting is set to automatically elapse every 60 minutes by default, but can be manually triggered if an administrator clicks **Refresh Cache** on the **Accounts** tab. On their next login, the user will be able to log in but will not see any entities that were assigned by the previous group membership.

- I expect my user to inherit group permissions, but I don't see these as part of **View Effective permissions** on the user. Why not?

Group membership is only determined when the user logs in, and it will display after login only until the cache is refreshed.