This example will demonstrate the "strategic merge" capability with "patchesStrategicMerge" tag in kustomization file.

Changes are organized in to separate files named as 
* set_memory.yaml - change the pod memory allocation
* set_replicas.yaml - change the number of replicas

> Note: 'test' namespace must pre-exist

To test run the below command
```
 kubectl apply -k sample3/
```
or 
```
 kustomize build sample3/ | kubectl apply -f -
```

Then check whether the deployment is successful with
```
  kubectl get all
```

Check whether the changes are applied with
```
  > kubectl describe deploy/nginx-deployment -n test

  Name:                   nginx-deployment
  Namespace:              test
  Selector:               app=nginx
  Replicas:               3 desired | 3 updated | 3 total | 3 available | 0 unavailable
  StrategyType:           RollingUpdate
  Pod Template:
    Labels:  app=nginx
    Containers:
    nginx:
      Image:      nginx:1.23.1
      Port:       80/TCP
      Host Port:  0/TCP
      Limits:
        cpu:     500m
        memory:  756Mi
      Requests:
        cpu:        250m
        memory:     512Mi
```
You can see all changes are applied above