# DJ Istio
Visualize your Service Mesh!

# Prerequisits
- Kubernetes cluster and access via kubectl (tested with version 1.13.7)
- Istio installed on Kubernetes (tested with verstion 1.2.5)

# Setup
- Create the service accounts
```kubectl apply -f base-setup/serviceaccounts.yaml``
- Install the different instrument containers
```kubectl apply -f base-setup/instruments/bass.yaml```
