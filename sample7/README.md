Change specific values of specific kubernetes entities with Patching. 
Patches are defined inline within the kustomization.yaml file

  ```
     kubectl apply -k sample7/
     kubectl get all -n test

     kubectl describe deployment nginx -n test | grep Name:
    ```