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
2️⃣ Edit the YAML file
Open cm.yaml in a text editor and make the following changes:

Remove all annotations (the entire annotations block under metadata).
This ensures the ConfigMap can be replaced cleanly.

Add TLSv1.2 to the ssl_protocols line inside the nginx.conf data.

The relevant part of the file should look like this after editing:

yaml
data:
  nginx.conf: |
    events {
        worker_connections 1024;
    }
    http {
        server {
            listen 443 ssl;
            server_name localhost;
            
            ssl_certificate /etc/nginx/ssl/tls.crt;
            ssl_certificate_key /etc/nginx/ssl/tls.key;
            ssl_protocols TLSv1.2 TLSv1.3;   # 👈 TLSv1.2 added
            
            location / {
                root /usr/share/nginx/html;
                index index.html;
            }
        }
    }
⚠️ Important: Keep a space between TLSv1.2 and TLSv1.3.

3️⃣ Replace the ConfigMap
Apply the updated configuration:

bash
kubectl replace -f cm.yaml
You should see output like:

text
configmap/nginx-config replaced
4️⃣ Restart the Deployment
For the changes to take effect, restart the NGINX deployment:

bash
kubectl rollout restart deployment nginx-static -n nginx-static
Wait for the new pods to be ready:

bash
kubectl rollout status deployment nginx-static -n nginx-static

✅ Verification
Get the Service IP
Find the ClusterIP of the NGINX service:

bash
kubectl get svc -n nginx-static
Example output:

text
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
nginx-service   ClusterIP   10.109.56.199   <none>        443/TCP   10m
Test TLSv1.2 Connection
Use curl to verify that TLSv1.2 is accepted:

bash
curl -k --tls-max 1.2 https://<SERVICE_IP>

