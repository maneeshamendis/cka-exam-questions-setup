# 🔧 Update NGINX ConfigMap to Enable TLSv1.2

<div align="center">
  
![CKA](https://img.shields.io/badge/CKA-Practice-blue?logo=kubernetes)
![Topic](https://img.shields.io/badge/Topic-ConfigMap%20Update%20%26%20TLSv1.2-success)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange)

</div>

This guide walks you through updating an existing `nginx-config` ConfigMap to **allow TLSv1.2** connections for an NGINX deployment. After the update, you'll verify that only TLSv1.2 is accepted using `curl`.

---

## 📋 Prerequisites

- A Kubernetes cluster with the `nginx-static` namespace and resources already created (via `setup.yaml`).
- The TLS secret `nginx-ssl` must exist in the namespace (see [TLS Secret Creation](#-optional-create-tls-secret-if-not-present)).
- `kubectl` configured to access your cluster.

> 💡 If you haven't set up the environment yet, apply the `setup.yaml` first:
> ```bash
> kubectl apply -f setup.yaml
> ```

---

## 🛠️ Step-by-Step Instructions

### 1️⃣ Export the current ConfigMap

Save the existing `nginx-config` ConfigMap to a YAML file:

```bash
kubectl get configmap nginx-config -n nginx-static -oyaml > cm.yaml
