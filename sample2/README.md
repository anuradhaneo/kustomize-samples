This example will simply add below to the 'nginx' deployment. 
* Add a label with key 'type' and the value as 'test'
* prefx the deployments with "test-"
* set the namespace of the deployment to "test", note the namespace must pre-exist

To test run the below command
```
 kubectl apply -k sample2/
```

or 
```
 kustomize build sample2/ | kubectl apply -f -
```

Then check whether the deployment is successful with
```
  kubectl get all
```

Check whether the label is applied with
```
  > kubectl get deployments -n test

  NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
  test-nginx-deployment   1/1     1            1           51s
```
and then check whether the above 3 things are applied
```
  > kubectl describe deploy/test-nginx-deployment -n test

  Name:                   test-nginx-deployment
  Namespace:              test
  CreationTimestamp:      Sun, 25 Sep 2022 20:03:44 +0530
  Labels:                 type=test
  Selector:               app=nginx,type=test
  Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
  StrategyType:           RollingUpdate
  RollingUpdateStrategy:  25% max unavailable, 25% max surge
  Pod Template:
    Labels:  app=nginx
            type=test
    Containers:
    nginx:
      Image:      nginx:1.23.1
      Port:       80/TCP
      Host Port:  0/TCP
      Limits:
        cpu:     500m
        memory:  512Mi
      Requests:
        cpu:        250m
        memory:     256Mi
```
You can see all three changes are applied above