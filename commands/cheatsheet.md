# listing images pulled by kubernetes
```
kubectl get node  -o json | jq -r '.items[].status.images[].names'
```
