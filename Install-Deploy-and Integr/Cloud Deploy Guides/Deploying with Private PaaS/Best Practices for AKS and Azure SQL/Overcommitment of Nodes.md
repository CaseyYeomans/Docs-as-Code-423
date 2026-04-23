# Overcommitment of Nodes

## Overcommitment of Linux Nodes

Clients must ensure the system nodes are not severely overcommitted. Some overcommitment is expected. Let the requests be the guide, as lower is better. 150-200% limits on Linux should be okay as long as the Requests do not go over 30%. If the requests are at 70-80%, clients must upgrade, as it is very likely that the limits will be well over 1000%. Unstable Linux nodes will result in unstable nginx operation (client's ingress) resulting in connectivity problems. Once connectivity problems start occurring, the method that is used to check whether Profisee is up and running (liveness probe) becomes unreliable, and the cluster will see that the Profisee container is unavailable and will restart it in order to bring it back to an operational state. In certain rare instances, clients can remove the liveness probe from the stateful set, but it is not recommended and not supported.

Microsoft recommends running three system nodes in a production environment. Two or fewer may be okay in Dev/Test depending on the client's particular requirements. System nodepool recommendations are found [here](https://urldefense.com/v3/__https:/learn.microsoft.com/en-us/azure/aks/use-system-pools?tabs=azure-cli__;!!NFWRZ6kECLqu!t3ViTadusQ2v5Q1Zqnva3XF4NBHyum6mf-_zzCYxZxMMGbiazhxo1qYoBMrjiQxLS38HE95mHFMznq1hoW0AfnCSOC0$). As mentioned on the linked page, 3 system nodes are recommended with 2v CPU sku at least, with 2x 4v CPU being recommended.

## Overcommitment of Windows Nodes

Do not overcommit memory in any circumstance. With Profisee running on the node, you should stick to about 95-97% of RAM at the max. The CPU might be slightly overcommitted. Please bear in mind the AKS reservations mentioned above.

### See more

[AKS API, Deployment and Upgrade Path](https://support.profisee.com/wikis/profiseeplatform/AKS_API_Deployment_and_Upgrade_Path)