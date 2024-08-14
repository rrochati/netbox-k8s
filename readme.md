# NetBox-k8s
Netbox setup on a Azure kubernetnes cluster, for lab purpose

## Notes
You need to create 2 Azure KeyVaults with **Vault access policy** as permission model:
1. postgre-secret
Secrets:
    * POSTGRES-HOST
    * POSTGRES-USER
    * POSTGRES-PASSWORD
2. netbox-secret
Secrets:
    * AUTH-LDAP-BIND-PASSWORD2
    * EMAIL-PASSWORD
    * NAPALM-PASSWORD
    * SECRET-KEY
    * SUPERUSER-PASSWORD
    * SUPERUSER-API-TOKEN

In this scenario the AKS will access the vaults using the Azure Keyvault Secrets Provider Identity, so make sure you give this identity the correct permissions.

You will also need the Azure Keyvault Secrets Provider Identity clientId and the Azure Tenant ID

## Installation

To get NetBox up and running on an existing Kubernetes cluster:

1. Deploy postgresql:
    * kubectl apply -f `postgre-basics.yaml` 
    * kubectl apply -n postgre -f `postgre-deployment.yaml`
    * If the namespace is changed, ensure all manifests are updated accordingly
2. Deploy netbox-k8s:
    * kubectl apply -f `netbox-basics.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-startup-configmap.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-deployment.yaml`

## References:
   * https://github.com/digitalocean/netbox/
   * https://netbox.readthedocs.io/en/stable/
   * https://github.com/netbox-community/netbox/
   * https://github.com/CENGN/netbox-kubernetes/
