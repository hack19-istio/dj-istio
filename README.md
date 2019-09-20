# DJ Istio
Visualize your Service Mesh!

# Overview
![Alt text](/docs/architecture.png?raw=true "Architecture overview")

# Prerequisits
- Kubernetes cluster and access via kubectl (tested with version 1.13.7)
- Istio installed on Kubernetes (tested with version 1.2.5)
```
kubectl create namespace istio-system
helm template install/kubernetes/helm/istio-init --name istio-init --namespace istio-system | kubectl apply -f -
helm template install/kubernetes/helm/istio --name istio --namespace istio-system | kubectl apply -f -
```

# Setup
### Initialization
Create some init config items like namespaces, serviceaccounts, etc.
```
kubectl apply -f base-setup/init.yaml
```
### Deploy the UI container
Including service and ingress gateway configuration
```
kubectl apply -f <(istioctl kube-inject -f base-setup/player-ui.yaml)
```
### Deploy the backend API container
Including services and ingress gateway configuration
```
kubectl apply -f <(istioctl kube-inject -f base-setup/player-backend.yaml)
```
### Deploy the different instrument containers
_bass_, and _piano_ exist as v1 and v2
```
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/rhodes.yaml)
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/bass.yaml)
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/hh.yaml)
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/kicksnare.yaml)
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/pad.yaml)
kubectl apply -f <(istioctl kube-inject -f base-setup/instruments/piano.yaml)
```
# Play with Istio features
### Mutual TLS
TODO

### A/B Testing
TODO

### ....
