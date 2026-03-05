# Add the official Argo CD Helm repository
helm repo add argo https://argoproj.github.io/argo-helm

# List Helm repositories
helm repo list

# Search for Argo CD charts
helm search repo argo

# List all versions of argo-cd chart
helm search repo argo/argo-cd --versions

# Filter for version 7.7.3
helm search repo argo/argo-cd --versions | grep 7.7.3

# Generate Helm template with CRDs disabled and save to file
helm template argocd argo/argo-cd --version 7.7.3 --set crds.install=false > argo-helm.yaml

# Apply the generated manifests to the cluster
kubectl apply -f argo-helm.yaml
