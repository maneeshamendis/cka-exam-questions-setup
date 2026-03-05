```yaml
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: high-priority
value: 1000000
preemptionPolicy: Never
globalDefault: false
description: "xxxxxxxxxxxxxxxxx"
```

to patch the deployment, execute the below ,, 

```bash
kubectl patch deploy busybox-logger -n priority -p '{"spec": {"template": {"spec": {"priorityClassName":"high-priority"}}}}'
```

##### 📝  NOTE : it's better to do a patch insted of editing the deployment. Once the patch is applied, do a rollout restart for the deployment. 
