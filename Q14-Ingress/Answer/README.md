```bash
kubectl get endpoints -n sound-repeater echoserver-service
```
### Ingress yaml 
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: echo
  namespace: sound-repeater
spec:
  rules:
  - host: mendis.org
    http:
      paths:
      - path: /echo
        pathType: Prefix
        backend:
          service:
            name: echoserver-service
            port:
              number: 8080
```
