#### Add the official Argo CD Helm repository
```bash
helm repo add argo https://argoproj.github.io/argo-helm
```
#### List Helm repositories
```bash
helm repo list
```
#### Search for Argo CD charts
```bash
helm search repo argo
```
#### List all versions of argo-cd chart
```bash
helm search repo argo/argo-cd --versions
```
#### Filter for version 7.7.3
```bash
helm search repo argo/argo-cd --versions | grep 7.7.3
```
#### Generate Helm template with CRDs disabled and save to file
```bash
helm template argocd argo/argo-cd --version 7.7.3 --set crds.install=false > argo-helm.yaml
```
#### Apply the generated manifests to the cluster
```bash
kubectl apply -f argo-helm.yaml
```

