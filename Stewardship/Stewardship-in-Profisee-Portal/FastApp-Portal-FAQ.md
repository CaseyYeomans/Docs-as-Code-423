# FastApp Portal FAQ

The following are answers to frequently asked questions about the Profisee FastApp Portal:

* Which web browsers are compatible with Profisee FastApp Portal?

> [!TIP]
> Currently, all major web browsers except for Internet Explorer are compatible with Profisee FastApp Portal.

* Can an administrator force a cache refresh for all users?

> [!TIP]
> Yes . If the administrator resets the server's Internet Information Services (IIS), the cache will refresh for all users. Note that Forms are not cached and therefore does not require a cache refresh. The next time the form is opened in the portal, the updated form will be used.

* > [!NOTE]
  > Why does nothing appear to happen when I click "Download to Excel?"

> [!TIP]
> Your WebSocket Protocol may not be enabled. You can enable this feature by opening Windows Features on your machine and navigating to Internet Information Services > World Wide Web Services > Application Development Features > WebSocket Protocol .

* > [!NOTE]
  > When adding an External type page item to my FastApp (e.g. www.bing.com ) the item saves, but the URL is not correct in the portal.

> [!TIP]
> When configuring an external page to the fastapp, it is important to use https:// format before the URL to ensure proper conversion. E.g. https://bing.com .

---