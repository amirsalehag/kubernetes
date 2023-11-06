# pg-restore a local dump into a pod inside k8s with kubectl

```bash
kubectl exec -in <namespace> <pod name> -- pg_restore --no-owner -U <user> --dbname postgres -c --create < /path/to/dumpfile
```
