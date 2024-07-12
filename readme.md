# NetBox-k8s
Simple Netbox setup on a local kubernetnes cluster

## Notes

* The NetBox deployment will work with existing redis and postgresql installations, just ensure that the configurations are changed in `netbox-configmap.yaml`, `netbox-secret.yaml` and `netbox-deployment.yaml`

## Installation

To get NetBox up and running on a Kubernetes cluster:

1. Deploy postgresql:
    * kubectl apply -f `postgre-namespace.yaml` 
    * kubectl apply -n postgre -f `postgre-secret.yaml`
    * kubectl apply -n postgre -f `postgre-deployment.yaml`
    * If the namespace is changed, ensure all manifests are updated accordingly
2. Deploy netbox-k8s:
    * kubectl apply -f `netbox-namespace.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-configmap.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-startup-configmap.yaml`
    * kubectl apply -n netbox-k8s -f `sso-saml2-configmap.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-secret.yaml`
    * kubectl apply -n netbox-k8s -f `netbox-deployment.yaml`

## References:
   * https://github.com/digitalocean/netbox/
   * https://netbox.readthedocs.io/en/stable/
   * https://github.com/netbox-community/netbox/
   * https://github.com/CENGN/netbox-kubernetes/
