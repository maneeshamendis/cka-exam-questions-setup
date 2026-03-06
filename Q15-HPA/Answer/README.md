```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: apache-server
  namespace: autoscale
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: apache-server
  minReplicas: 1
  maxReplicas: 4
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
  behavior:
    scaleDown:
      stabilizationWindowSeconds: 30
```
```bash
kubectl get hpa -n autoscale
```
```text
NAME            REFERENCE                  TARGETS              MINPODS   MAXPODS   REPLICAS   AGE
apache-server   Deployment/apache-server   cpu: <unknown>/50%   1         4         2          2m39s
```
