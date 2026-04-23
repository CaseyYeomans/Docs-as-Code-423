# AKS API, Deployment and Upgrade Path

Microsoft recommends a paid tier API for production environments. If clients run a single container workload (Profisee) a free tier is usually sufficient. The choice is up to the client. Please be aware that Microsoft, on the paid tier, provides an uptime SLA for the API server endpoint only, not the underlying Linux of Windows nodes. Once again, the underlying Linux and Windows nodes have no SLA, regardless of if they are paid vs free, meaning some network intermittency is expected. More information can be found [here](https://urldefense.com/v3/__https:/learn.microsoft.com/en-us/azure/aks/free-standard-pricing-tiers__;!!NFWRZ6kECLqu!t3ViTadusQ2v5Q1Zqnva3XF4NBHyum6mf-_zzCYxZxMMGbiazhxo1qYoBMrjiQxLS38HE95mHFMznq1hoW0AejkVWLo$).

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i99150857fa70415c.png)

## Deployment and Upgrade Path

To deploy:

1. For the jump from AKS version 1.23 to 1.24 - it is suggested to run these commands before the AKS upgrade (can be done after the upgrade, but immediately after). This will retain nginx in an operational state as it will ensure that the TCP health probes for your ingress are retained. As of 1.24, AKS deploys HTTP/HTTPS probes for ingress. Profisee is in the process of updating to those but they are not generally available.
1. elm repo -n profisee add ingress-nginx [https://kubernetes.github.io/ingress-nginx](https://urldefense.com/v3/__https:/kubernetes.github.io/ingress-nginx__;!!NFWRZ6kECLqu!t3ViTadusQ2v5Q1Zqnva3XF4NBHyum6mf-_zzCYxZxMMGbiazhxo1qYoBMrjiQxLS38HE95mHFMznq1hoW0Ajlb4U6Q$)
2. helm repo update
3. helm get values -n profisee nginx -o yaml > nginx-values.yaml
4. helm upgrade --install -n profisee nginx ingress-nginx/ingress-nginx --values nginx\_x0002\_values.yaml --set controller.service.appProtocol=false
2. For the jump from 1.24 to 1.25 and up: As of v.1.25.x the default Windows nodepool OS-Sku is Server 2022. That, unfortunately, is incompatible with Profisee's present container image, which is on Server 2019. Should clients need to change the size of the Windows nodepool please deploy a new one by manually configuring one via the cloudshell or powershell (for Private PaaS, clients need to be on a jumpbox and use powershell). For client's current upgrade, this will not be required as their node is already on Windows 2019.
1. az aks nodepool add --cluster-name <clustername> --resource-group <name of res group> --
name <name of new nodepool-6charmax> --os-type Windows --os-sku Windows2019 --node\_x0002\_vm-size Standard\_D8as\_v5 --node-count 1
2. As of the next Profisee release (23r2) the underlying container will become Server 2022 and
the change will have to be made using the same command but using --os-sku Windows
2022.

### See more

[PaaS Resource Management and Database Management](https://support.profisee.com/wikis/profiseeplatform/PaaS_Resource_Management_and_Database_Management)