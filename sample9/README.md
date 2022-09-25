## Overlays

Implement real world example using Overlays. Overlays implement the concept of configurations based on separate environments such as dev/statging and pod.
Change the values as requered in sample9/overlays/<environment>/patches directory
  ```
     kubectl apply -k sample9/overlays/staging
     kubectl get all -n test
     kubectl describe deployment redis -n test | grep Replicas:

     kubectl apply -k sample9/overlays/prod
     kubectl get all -n prod
     kubectl describe deployment redis -n prod | grep Replicas:
   ```

#### output of "kubectl get all -n test" after running "kubectl apply -k sample9/overlays/staging"


```
NAME                                    READY   STATUS    RESTARTS   AGE
pod/redis-db-5b684b7676-cwwmf           1/1     Running   0          13s
pod/redis-db-5b684b7676-xx9gf           1/1     Running   0          13s
pod/nginx-deployment-7dfbbd4578-m7t7b   1/1     Running   0          13s
pod/nginx-deployment-7dfbbd4578-9tqcn   1/1     Running   0          13s
pod/redis-db-5b684b7676-kb9d7           1/1     Running   0          13s

NAME               TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/nginx      NodePort   10.43.22.213   <none>        80:32500/TCP     13s
service/redis-db   NodePort   10.43.36.47    <none>        6379:32379/TCP   13s

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-deployment   2/2     2            2           13s
deployment.apps/redis-db           3/3     3            3           13s

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-deployment-7dfbbd4578   2         2         2       13s
replicaset.apps/redis-db-5b684b7676           3         3         3       13s
```