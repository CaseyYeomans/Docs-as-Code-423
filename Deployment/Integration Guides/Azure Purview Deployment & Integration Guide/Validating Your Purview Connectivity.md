# Validating Your Purview Connectivity

Once your Profisee Platform instance has been configured to communicate with Purview, you can test the connectivity using the governance health check. This will confirm that the Profisee Platform can successfully connect to Purview and will confirm that the Purview cache has been loaded with counts of all the Profisee assets published to Purview. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2b3c0a2cefee9e1f.png)

You can also access the REST endpoint associated with the newly applied Governance Service. To perform a basic validation:

1. Open a browser and navigate to the Profisee API swagger page.
E.g., *https://{your\_server\_name}/Profisee/rest*![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia2d2239be76c1556.png)

2. In the **Governance** section, expand the **Get /{version}/Governance/instances** request and click to "try it out".
3. Enter your **Profisee user client ID** and Execute.
4. It should return a response that appears something like the following:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5ad9fbc2d45abf7b.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5ad0624e0715e5ff.png)

If you get a valid response to the instance request, Profisee is communicating successfully with Purview.