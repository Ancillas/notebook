# Useful Kubernetes Commands

## Get Crashed Pod's Logs

```
kubectl describe pod <pod> --namespace=kube-system
# Print logs from exited container
kubectl logs nginx-78f5d695bd-czm8z -p
```

[Container Logs · The Kubectl Book](https://kubectl.docs.kubernetes.io/pages/container_debugging/container_logs.html)

## Create Persistent Volume in Longhorn

Create yaml file with resource definition.

`postgres-pvc.yaml`

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: postgresql-pv
spec:
  storageClassName: longhorn
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  volumeMode: Filesystem
  persistentVolumeReclaimPolicy: Retain
  csi:
    driver: driver.longhorn.io
    fsType: ext4
    volumeAttributes:
      numberofReplicas: '3'
      staleReplicaTimeout: '2880'
    volumeHandle: postgres-longhorn-volume
```

Then apply it

```
kubectl apply -f postgres-pvc.yaml
```

## Kubectl Ignore Bad Cert for Test Environments

Don't do this in production.  Use this if you want to force a connection and skip certificate validation.

```
kubectl --insecure-skip-tls-verify apply -f postgres-pvc.yaml
```
