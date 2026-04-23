# Configuring "Next Hop" Ingress and Egress

### Ingress Requirements

When configuring the rules for traffic inbound into the AKS cluster, you will need to allow HTTPS traffic to reach the cluster's *kubernetes-internal* Load Balancer IP.

### External Service Requirements for Deployment and Operations

Our private PaaS deployment will also have many outbound network requirements. The three tables on the following pages identify the external services on which the AKS cluster and Profisee instance depends. These are categorized as follows:

1. Kubernetes Infrastructure Egress Requirements: domains that must be reachable for AKS to spin up successfully
2. Profisee Infrastructure Egress Requirements: domains that must be reachable for the Profisee pod to spin up within AKS
3. Profisee Application Egress Requirements: domains that must be reachable for Profisee's software to run correctly after setup

The columns in these tables outline the following:

- **Name**: Describes the external dependency.
- **Optional**: Indicates if the dependency is mandatory and must be provided for the system to operate correctly.
- **Variability Type**: Indicates the type of variability of the service endpoint URI.
- **Fixed**: Indicates that the URI specified in the Service Endpoint/Endpoint Template column is a fixed (i.e., constant) value and should be used as-is
- **Varies by Customer**: Indicates that the URI specified is a template and the <PLACEHOLDER> value will vary by customer installation.
- **Varies by Type**: Indicates that there are two or more options that the system supports, and the URI varies by the type selected.
- **Service Endpoint/Endpoint Template**: Identifies the service URI or URI template that should be accessible within the scope of the dependency category. Where the type is Fixed, the URI should be used verbatim. Where the type varies, the <PLACEHOLDER> template should be replaced with the service that applies for the installer's specific environment OR the type-specific URI.

Where possible we have included the full url: be aware that some Azure resources will only allow you to filter traffic on the base domain (ex. Azure Premium Firewall will allow you to do URL filtering, whereas Standard will not.)

### Kubernetes Infrastructure Egress Requirements

The following table identifies external services upon which Azure Kubernetes Services depends when managing cluster operations. These dependencies are not specific to the Profisee Platform. Therefore, Profisee recommends that the installer/operator be very familiar with the setup and operations of an AKS cluster. If using an Azure Firewall as a "next hop" appliance, you may also consider using the AzureKubernetesService FQDN tag.

Refer to the following URL for detailed instructions and guidance related to AKS:

<https://docs.microsoft.com/en-us/azure/aks/limit-egress-traffic>

If you wish to customize your deployment by using Azure Monitor, Defender for Containers, or Cluster Extensions, you will need to have access to additional services beyond what is included in this table. Please refer to the Azure documentation on what to add.

| | | | |
| --- | --- | --- | --- |
| **Name** | **Optional** | **Variability** **Type** | **Service Endpoint/Endpoint Template** |
| Microsoft Container Registry Images | No | Fixed | mcr.microsoft.com:443 |
| Microsoft Container Registry Storage | No | Fixed | \*.data.mcr.microsoft.com:443 |
| Azure API | No | Fixed | management.azure.com:443 |
| Microsoft Packages Repo | No | Fixed | packages.microsoft.com:443 |
| Required Binaries | No | Fixed | acs-mirror.azureedge.net:443 |
| Windows Related Binaries | No | Fixed | onegetcdn.azureedge.net:443 go.microsoft.com:443 \*.mp.microsoft.com:80 www.msftconnecttest.com:80 ctldl.windowsupdate.com:80 |
| CSI Secret Store | No | Fixed | vault.azure.net:443 |
| Linux Security Updates | Yes | Fixed | security.ubuntu.com:80 azure.archive.ubuntu.com:80 changelogs.ubuntu.com:80 |
| Custom DNS Servers | Yes | Varies by Customer | <IPAddress>:53 |

### Profisee Infrastructure Egress Requirements

When it comes to Profisee, we normally allow all outbound HTTP and HTTPS traffic. If your organization has stricter security requirements you may have to lock this further down. If your SQL instance, Storage Account, Key Vault, or Purview instance is separated from the AKS cluster by a firewall or any other device that restricts traffic, you will also have to add additional rules allowing the relevant traffic to flow through. Be aware that it is not recommended to use Let's Encrypt if you are using locked down egress rules, as it will not allow for automatic renewals. If you want to use Let's Encrypt, consider using a HTTP or DNS challenge instead of ACME challenge.

The following table identifies the dependencies that are specific to the ***provisioning*** of the Profisee Platform. These services support the configuration and start-up of a Profisee Platform instance.

| | | | |
| --- | --- | --- | --- |
| **Name** | **Optional** | **Variability** **Type** | **Service Endpoint/Endpoint Template** |
| Profisee Azure Container Registry | No | Fixed | profisee.azurecr.io:443 |
| Profisee Chart | No | Fixed | profisee.github.io/kubernetes:443 |
| Profisee ACR Image file location | No | Fixed | \*.blob.core.windows.net:443 |
| Nginx | No | Fixed | kubernetes.github.io/ingress-nginx:443 |
| Nginx | No | Fixed | k8s.gcr.io:443 |
| Nginx | No | Fixed | storage.googleapis.com:443 |
| Nginx | No | Fixed | registry.k8s.io:443 |
| Nginx | No | Fixed | \*.docker.pkg.dev:443 |
| Nginx | No | Fixed | \*.amazonaws.com |
| Nginx | No | Fixed | \*.docker.pkg.dev:443 |
| Nginx | No | Fixed | production.cloudflare.docker.com |
| Windows node related | No | |