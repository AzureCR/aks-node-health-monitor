# Installing Kubernetes Node Health Monitoring on AKS
Steps to install [health-monitor.sh](https://github.com/kubernetes/kubernetes/blob/master/cluster/gce/gci/health-monitor.sh) on Azure Kubernetes Service (AKS) cluster nodes to ensure the health of docker and kubelet.

## Prerequisites
- [Azure Kubernetes Service (AKS) cluster](https://docs.microsoft.com/en-us/azure/aks/)
- [azure-cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

## Install health-monitor.sh to an AKS node
``` sh
export SUBSCRIPTION_ID=<azure subscription id>
export RESOURCE_GROUP=<MC_ aks resource group>
export VM_NAME=<aks node name>
az vm run-command invoke -g "${RESOURCE_GROUP}" -n "${VM_NAME}" --subscription-id "${SUBSCRIPTION_ID}" --command-id RunShellScript --scripts "curl -s https://raw.githubusercontent.com/juan-lee/aks-node-health-monitor/master/install | bash -s"
```
