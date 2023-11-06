# Restore a local dump into a pod inside k8s with kubectl

* postgresql

```bash
kubectl exec -in <namespace> <pod name> -- pg_restore --no-owner -U <user> --dbname postgres -c --create < /path/to/dumpfile
```
* mongodb

```bash
kubectl exec -in <namespace> <pod name> -- mongorestore --quiet --host='127.0.0.1:27017' --authenticationDatabase=admin --username=<username> --password=<password> --gzip --archive < /path/to/dump 
```
