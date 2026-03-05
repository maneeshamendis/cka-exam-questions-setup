#### calico : https://raw.githubusercontent.com/projectcalico/calico/v3.31.4/manifests/tigera-operator.yaml 
#### fannel : kubectl apply -f https://github.com/flannel-io/flannel/releases/latest/download/kube-flannel.yml

##### download both the files using wget. cat the files and search for Netowork 

```bash
cat kube-flannel.yml | grep policy
```
```bash
cat tigera-operator.yaml | grep policy
```

Out of these, calico supports for network policy. 

#### apply it. 
```bash
kubectl apply -f tigera-operator.yaml
```

### ⚠️ ⚠️ NOTE : you will get an error like below 
#### 🛠️🛠️🛠️🛠️🛠️ 
```bash
The CustomResourceDefinition "installations.operator.tigera.io" is invalid: metadata.annotations: Too long: may not be more than 262144 bytes
```

#### Execute replace command with --force flag    ✅ 
```bash
kubectl replace -f tigera-operator.yaml --force 
```

### ⚠️ ⚠️ NOTE : there will be CIDR missmatches as well.. if there is any fix it before apply 
```bash
kubectl get po --all-namespces  
```
