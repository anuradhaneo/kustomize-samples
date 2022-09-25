This example shows how multiple K8S manifest files are linked together to form a single unit of configuration script.

This allowes multiple yaml files stored within different directory paths linked togerther. This makes all the K8S manifests executable in one 'kubectl apply' command.

K8S manifests are organized in to separate files named as 
* db/redis.yaml - deploy an in-memory redis database
* lb/nginx.yaml - deploy a nginx instance with default configurations

> Note: 'test' namespace must pre-exist

To test run the below command
```
 kubectl apply -k sample4/
```
or 
```
 kustomize build sample4/ | kubectl apply -f -
```

Then check whether the deployments are successful with
```
  > kubectl get deployments -n test

  NAME               READY   UP-TO-DATE   AVAILABLE   AGE
  nginx-deployment   1/1     1            1           12s
  redis-db           1/1     1            1           12s
```
You can see all changes are applied above