Change specific values of specific kubernetes entities with Patching, and patches defined in separate files

  ```
     kubectl apply -k sample8/
     kubectl get all -n test

     kubectl describe deployment nginx -n test | grep Replicas:
    ```