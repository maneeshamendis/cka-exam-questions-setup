#### get the deploy into a yaml file 
```bash
kubectl get deploy synergy-logger -n synergy -oyaml > aa.yaml
```

#### add the sidecar contaner and volume mounts ( only add the mention lines,, ) 
```yaml
spec:
  replicas: 1
  selector:
    matchLabels:
      app: synergy
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      labels:
        app: synergy
    spec:
      containers:
      - name: myapp
        image: alpine:latest
        command: ['/bin/sh', '-c', "tail -n+1 -f /var/log/synergy-leverager.log"]
        volumeMounts:  # 👈
         - name: data  # 👈
           mountPath: /var/log # 👈
      - command:
        - /bin/sh
        - -c
        - |
          while true; do
            echo "$(date) - Synergy leverager is running" >> /var/log/synergy-leverager.log
            sleep 5
          done
        image: busybox # 👈
        volumeMounts: # 👈
         - name: data # 👈
           mountPath: /var/log # 👈
        imagePullPolicy: Always
        name: sidecar  # 👈
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      volumes:          # 👈
        - name: data    # 👈
          emptyDir: {}  # 👈
