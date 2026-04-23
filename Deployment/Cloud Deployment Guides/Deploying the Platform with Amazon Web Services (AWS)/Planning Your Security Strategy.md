# Planning Your Security Strategy

There are two critical aspects of security planning related to the Profisee Platform as it pertains to deployment in AWS.

1. Will your organization provide its own certificate that has been provided by a legitimate certificate authority or do you want to automatically provision certificates during the cluster provisioning process?
2. What OIDC/OAUTH2 provider(s) do you want to use to authenticate users when they access the platform through FastApp Studio or FastApp Portal?

Both aspects affect your configuration in the **Settings.yaml** file.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i95adf012f0d5cd3d.png)

### Deciding on Your Certificate Source

The Profisee Platform requires the use of certificates to ensure secure communications to and from the platform. You can provide your own certificates, or you can allow certificates to be obtained automatically during the cluster provisioning process using [Let's Encrypt](https://letsencrypt.org/).

There are two steps required to use Let's **Encrypt**:

1. You must set the **useLetsEncrypt** setting to **true i**n the **Settings.yaml.** See snippet below:
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i55e766a48959144.png)
2. You must install [cert-manager](https://cert-manager.io/) as part of your cluster deployment. See detailed instructions titled ***(Optional) - Install cert-manager*** for **Let's Encrypt** in the Deployment section of [Deploy Profisee platform on to AWS Elastic Kubernetes services (EKS)](https://github.com/Profisee/kubernetes/tree/master/AWS-EKS-CLI#deploy-profisee-platform-on-to-aws-elastic-kubernetes-services-eks) article in Profisee's GitHub site.

If you choose to supply your own certificate, you will need to obtain a valid certificate along with its private key from a Trusted Certificate Authority (TCA). Depending on the sophistication of your organization, it may have its own TCA that issues valid certificates within your company. Otherwise, you can use a commercial TCA and pay a small fee for a trusted certificate.

To configure certificate use for your cluster, extract the text of both certificate and private key from your certificate file (i.e. .pfx file) and record them in the **Settings.yaml** file in preparation for the deployment. You can use utilities such as [OpenSSL](https://www.openssl.org/) to extract the certificate file (.crt) and private key file (.key) from the associated .pfx file.

You will need the password associated with the certificate to extract the certificate and private key details. The provider/creator of the certificate should be able to supply this to you or you can ask them to extract the certificate and private key details and send them to you instead of the .pfx file.

The figure below shows the content that must be copied from the extracted certificate and private key files:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iadc483229e46bfb9.png)

The certificate and private key must be placed into the **Settings.yaml** file as the values for the **tlsCert** and **tlsKey** settings, respectively. See the snippet below for an example of how to configure the certificate values.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib5a2c2bf4dd8963e.png)

### Setting Up Your OIDC Authentication Providers

The Profisee Platform authenticates users using one or more OIDC/OAUTH2 authorities. Although the Profisee Platform has been tested against Azure Active Directory, Okta, and Google, you are free to add other OIDC/OAUTH2 authorities as your corporate requirements dictate. However, you and your team will need to identify the settings to use for those 3rd-party authorities as needed. In this topic, we cover how to set up your primary and secondary authorities using AAD, Okta, and Google specifically.

The **Settings.yaml** file contains two sections in which you specify your OIDC authority settings. These are shown in the snippet below. The top-most **oidc** section is where you specify the OIDC settings for your primary authority. The lower **oicdFileData** section is where you specify secondary authorities.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i73759e0948133dd0.png)

Profisee's **Settings.yaml** template contains an empty **oidcFileData** section as shown above. This indicates that there are no secondary OIDC authorities configured. If you want to include alternate authorities, they should be added to the **oidcFileData** as specified in the snippet below. This example shows the use of Okta and Google as secondary and tertiary authorities respectively:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ida4978f535606435.png)