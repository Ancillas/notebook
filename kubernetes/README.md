# Useful Kubernetes Commands

## Get Crashed Pod's Logs

```
kubectl describe pod <pod> --namespace=kube-system
# Print logs from exited container
kubectl logs nginx-78f5d695bd-czm8z -p
```

[Container Logs · The Kubectl Book](https://kubectl.docs.kubernetes.io/pages/container_debugging/container_logs.html)
