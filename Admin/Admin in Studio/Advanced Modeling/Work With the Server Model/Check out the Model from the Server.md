# Check out the Model from the Server

Check out the system model when you open it from the server. The model is flagged with status and user's name, to alert other users that the model is checked out. Only one user can check out the model at a time. The model must be checked out to enable publishing changes to the original server. Multiple users cannot simultaneously check out and edit the system model, and publish potentially conflicting changes.

The model can be opened without being checked out, but the model must be checked out prior to publishing it to the server.

To check out the model for editing in the Advanced Modeling tab:

1. Click **Open** on the Advanced Modeling toolbar.
2. Click **Open from Server** on the menu.
3. Select **Check out the model when opening**.
4. Click **OK**.

The model opens in the modeling surface.

The system model is checked out in many application feature areas whenever a user may potentially make a metadata change.

If a staging batch is running for an entity in the system model, you will not be able to check out the model until staging completes. This situation can occur when a matching or verification strategy is running for an entity.

When you check out the system model, the server flags the model as checked out so that multiple users do not attempt to edit it at the same time.

If you do not select Check out the model when opening, the model is not locked and other users with the System Administrator role can open the model without first seeing a warning.

It is possible to override the model checkout. As a best practice, first check with anyone who currently has a checked out model before overriding the checkout.

No other user can make changes to the model using any other feature area when it is checked out unless they override the checkout first. This includes model modifications that occur when conducting Address Verification or Matching. The user who has the model checked out can make changes to it elsewhere in the application (using Adaptive Modeling, for example).