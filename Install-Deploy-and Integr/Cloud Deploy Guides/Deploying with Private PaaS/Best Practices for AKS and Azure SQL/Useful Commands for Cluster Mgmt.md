# Useful Commands for Cluster Management

Profisee uses the common command line tool kubectl. Here's a cheat sheet with a lot of the commands.
This is by no means an exhaustive list.
#To display all nodes in a cluster
Kubectl get nodes
#To display all pods in a cluster and all pods in a specific namespace
Kubectl get pods -A #for all namespaces
Kubectl get pods -n profisee #for the profisee namespace
#To describe something, whether that is a pod, node, ingress, rule, etc.
Kubectl describe node <nameofnode>
Kubectl describe pod -n profisee profisee-0 #this describes the profisee-0 pod in the profisee namespace
#To get the allocatable resources for a Windows node
Kubectl get nodes #this will display all nodes, look for the Windows named node, it'll most likely include win
it its name

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idc6f05cc39e53c75.png)
Kubectl describe node <InsertWinNodeNameHere> #look for the allocatable resources section. Subtract 2G
from the memory number.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ifcf45ba0a5e3efc0.png)
#You will now have to edit Profisee's stateful set in the portal (under Cluster, Workloads, Stateful Sets) and
adjust the Limits until you are below 100%, see below. Here, Profisee consumes max 3.8cores and 10.2G of
ram and the node reports 98% max load for both ram and CPU. The Windows SKU here is B4ms, 4 cores
and 16G of ram (it's a test env, do not use B SKUs). As you can see, Kubernetes takes a lot from the smaller
SKUs. The situation gets better with bigger SKUs, though.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iddf33a6df46d9578.png)
#List all deployments in a namespace
Helm list -n profisee #this will show profiseeplatform, nginx and, depending on whether Let's Encrypt is
used or not, cert-manager, along with their chart versions.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i440419a7427a449e.png)
#Upgrades for those can be done by first exporting the current configuration using:
Helm repo update #To pull the latest helm charts
Helm get values -n profisee nginx -o yaml > nginx-values.yaml #This will create the nginx-values.yaml file.
Follow this with the upgrade command below.
Helm upgrade --install -n profisee nginx ingress-nginx/ingress-nginx --values nginx-values.yaml #You can
also add --set controller.service.appProtocol=false to this command so that TCP probes are retained. This is
required for the 1.23 to 1.24 upgrade. Once we switch to HTTP/HTTPS probes, we will provide guidance on
how to switch back.
#Cert-manager follows same command structure, but the file name would be certmanager-value.yaml.
Technically, it can be any name, so long as it matches between the export and upgrade commands.

## Repositories for Various Components

Profisee uses the following components:
Nginx - for ingress, [Documentation](https://kubernetes.github.io/ingress-nginx/) and its [GitHub page](https://github.com/kubernetes/ingress-nginx/).
Pod-Identity - deprecated, replaced by Workload identity. We are in the process of updating our documentation on what the changes are, they are minimal.
Cert-Manager - for Let's Encrypt Certificates and their renewals. [Documentation](https://cert-manager.io/docs/), [compatibility matrix](https://cert-manager.io/docs/installation/supported-releases/) and
[GitHub page](https://github.com/cert-manager/cert-manager).