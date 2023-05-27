A cheatsheet for frequently used [[Kubernetes]] commands.

### Get commands with basic output
```bash
kubectl get services                          # List all services in the namespace
kubectl get pods --all-namespaces             # List all pods in all namespaces
kubectl get pods -o wide                      # List all pods with more details
kubectl get deployment <pod-name>             # List a particular deployment
kubectl get pods                              # List all pods in the namespace
kubectl get pod <pod-name> -o yaml            # Get a pod's YAML
```

### Describe commands with verbose output
```bash
kubectl describe nodes <node-name>
kubectl describe pods <pod-name>
```

### Logs
```bash
kubectl logs <pod-name>                       
kubectl logs --since=1h <pod-name>            # Get te log items of the last hour
kubectl logs --tail=20 <pod-name>             # Get the last 20 log items
```
