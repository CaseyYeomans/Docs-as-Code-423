# Planning Your HTTPS Security

For clients of the Profisee cluster to communicate securely with the platform, you must enable HTTPS communications when provisioning the cluster. Although Profisee supports insecure communications over HTTP, this is intended to simplify evaluations and internal non-production uses where security of the data and communications is not essential.

Profisee strongly recommends the use of HTTPS for **all** installed instances of the platform. it is essential that all production instances enable secure communications via HTTPS to ensure the safety and integrity of the data and the solution.

The following process diagram outlines the decision points and actions related to HTTPS security:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib5f15304b88c0c1c.png)

The answer to the question **Enable HTTPS Communications?** should be noted for use with the **Https Configure** property of the ARM template.

**If you choose 'Yes,' you must:**

- Obtain a valid certificate along with its private key from a Trusted Certificate Authority (TCA). Depending on the sophistication of your organization, it may have its own TCA that issues valid certificates within your company. Otherwise, you can use a commercial TCA and pay a small fee for a trusted certificate.
- Extract the text of both the certificate and private key and record them in a text file for use in the **Https Certificate** and **Https Certificate Private Key** properties of the ARM template when performing the deployment. The certificate is a plain text file (.txt) that can be opened in a plain text reader such as Notepad. The Certificate begins with **-----BEGIN CERTIFICATE-----**and the Private Key begins with the text **-----BEGIN PRIVATE KEY-----**. The Certificate and Private Key end with the text **----END----**. All of this text must be included in the above properties.

**If you choose 'No,' then:**

- Planning for HTTPS is complete. You will be able to leave the **Https Certificate** and **Https Certificate Private Key** properties of the ARM template blank. However, know that all communications to and from the Profisee cluster will be open to inspection by third-parties.

As part of this planning process, you should now have identified the following properties of the Profisee ARM template:

- Https Configure (Y/N)
- Https Certificate
- Https Certificate Private Key

You may now continue to [Planning Your Cluster & Network Requirements](https://support.profisee.com/wikis/profiseeplatform/planning_your_cluster_and_network_requirements) or return to [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template).

### See more

- [Planning Your AKS ARM Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)