This example will simply add a K8S label to the 'nginx' deployment. Label name added is 'type' and the value is 'test'

To test run the below command
```
 kubectl apply -k sample1/
```

or 
```
 kustomize build sample1/ | kubectl apply -f -
```

Then check whether the deployment is successful with
```
  kubectl get all
```

Check whether the label is applied with
```
  > kubectl get deployment/nginx-deployment --show-labels

  NAME               READY   UP-TO-DATE   AVAILABLE   AGE   LABELS
  nginx-deployment   1/1     1            1           11m   type=test
```
and 
```
  > kubectl get po --show-labels

  NAME                                READY   STATUS    RESTARTS   AGE   LABELS
  nginx-deployment-75d87c867b-c4lgc   1/1     Running   0          11m   app=nginx,type=test
```