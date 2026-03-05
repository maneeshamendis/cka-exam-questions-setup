📝 ANSWER ... 
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mariadb-pvc
  namespace: mariadb
spec:
  accessModes:
    - ReadWriteOnce
  volumeMode: Filesystem
  resources:
    requests:
      storage: 250Mi
  storageClassName: ""
  volumeName: maria-pv
```

after apply , do a rolllout restart for the deployment if the pod did not come up 

```bash
kubectl rollout restart deploy mariadb-deploy -n mariadb
```
