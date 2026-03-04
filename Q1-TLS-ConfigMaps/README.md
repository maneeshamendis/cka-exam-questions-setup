# 🛡️ NGINX TLS & ConfigMap Update Practice

<div align="center">
  
![CKA](https://img.shields.io/badge/CKA-Practice-blue?logo=kubernetes)
![Topic](https://img.shields.io/badge/Topic-ConfigMap%20%26%20TLS-success)
![Level](https://img.shields.io/badge/Level-Intermediate-orange)

</div>

This folder contains a hands-on scenario to practice **updating a ConfigMap** and **enabling TLSv1.2** in an NGINX deployment. You'll also create a TLS secret and test the secure connection.

---

## 📋 Scenario Overview

- A Deployment named `nginx-static` runs in the `nginx-static` namespace.
- It uses a ConfigMap called `nginx-config` for its configuration.
- **Task**: Update the ConfigMap to **allow TLSv1.2 connections**.
- Additionally, you need to create a TLS secret named `nginx-ssl` using provided certificates.

After applying the changes, verify with a `curl` command that only TLSv1.2 is accepted.

---

## 🧱 Prerequisites

- A Kubernetes cluster (local, cloud, or [KillerCoda](https://killercoda.com/playgrounds))
- `kubectl` configured
- Basic understanding of ConfigMaps, Secrets, and Deployments

---

## 🚀 Step-by-Step Instructions

### 1️⃣ Set up the environment

Apply the `setup.yaml` file to create the initial resources:

```bash
kubectl apply -f setup.yaml

# Generate certificate (run in your terminal)
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout tls.key -out tls.crt \
  -subj "/CN=localhost/O=test"

# Create the secret in the namespace
kubectl create secret tls nginx-ssl \
  --cert=tls.crt --key=tls.key \
  -n nginx-static
