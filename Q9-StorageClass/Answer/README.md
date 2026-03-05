### Note : First change the SC as the defult in the cluster. 
```bash
kubectl edit sc local-path
```
```yaml
  annotations:
    storageclass.kubernetes.io/is-default-class: "false" # 👈 this should be false 
```
#### yaml file for create the new SC 
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: local-path2
  annotations:
    storageclass.kubernetes.io/is-default-class: "true"
provisioner: rancher.io/local-path
reclaimPolicy: Delete
volumeBindingMode: WaitForFirstConsumer
```

