# Deployment rollback

We can rollback a deployment to whatever version we want if we have its version history available.  
* Rollback to its latest version:
```
kubectl rollout undo deployment <deployment name>
```
* Checking Rollout History of a Deployment:
```
kubectl rollout history deployment/<deployment name>
```
* Checking Rollout History of a Deployment:
```
kubectl rollout history deployment/<deployment name>

<output of an nginx example>

deployments "nginx-deployment"
REVISION    CHANGE-CAUSE
1           kubectl apply --filename=https://k8s.io/examples/controllers/nginx-deployment.yaml
2           kubectl set image deployment/nginx-deployment nginx=nginx:1.16.1
3           kubectl set image deployment/nginx-deployment nginx=nginx:1.161
```
* Rollback to a specific revision by specifying it with `--to-revision`:
```
kubectl rollout undo deployment/<deployment name> --to-revision=2
```
## 
`CHANGE-CAUSE` is copied from the Deployment annotation kubernetes.io/change-cause to its revisions upon creation. You can specify the `CHANGE-CAUSE` message by:

* Annotating the Deployment with kubectl annotate deployment/nginx-deployment kubernetes.io/change-cause="image updated to 1.16.1"
* Manually editing the manifest of the resource.  
[link](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-back-a-deployment).
