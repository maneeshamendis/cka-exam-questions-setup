## 📋 Question :- 
Using kubectl, create a list of all cert-manager Custom Resource Definitions (CRDs ) and save it to ~/resources.yaml .
Using kubectl, extract the documentation for the subject specification field of the Certificate Custom Resource and save it to ~/subject.yaml

### SETUP :- 
Execute the below command on your Terminal 
```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.0/cert-manager.yaml
```
### ✅  Answer 
```bash
kubectl get crd | grep cert-manager > ~/resources.yaml
```
```bash
kubectl explain certificate.spec.subject > ~/subject.yaml
```
