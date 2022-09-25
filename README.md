# kustomize-samples

Some sample Kubernetes projects using Kustomize

## Install Kustomize
Install the customize tool as per your OS using the official guide below

https://kubectl.docs.kubernetes.io/installation/kustomize/

I used below since im using MacOS
```
brew install kustomize
```

However, it is not mandatory to install Kustomize as above since, K8S v1.14, Kubectl also natively supports the management of Kubernetes objects using a kustomization file.

## Check the final code before executing

Run the below command in the location of kustomization.yaml file
  ```
     kustomize build <path>
```
This will output the parsed kubernetes manifests on to the terminal itself, so that you can validate them before "kubectl apply"

## Samples Provided

- Sample1 : Simple kustomization of a nginx deployment that adds a label
  ```
     kubectl apply -k sample1/
     kubectl get all -n test
    ```

- Sample2 : Like similar to Sample1, adds few more additional common transformers like namespace and a prefix to the deployment
  ```
     kubectl apply -k sample2/
     kubectl get all -n test
    ```

- Sample 3 : Introduces Strategic-Merge patch that changes the replica count of the nginx deployments and also increases the memory resource allocations
  ```
     kubectl apply -k sample3/
     kubectl get all -n test
    ```

- Sample 4 : Organize K8S manifests in to a app specific structures
  ```
     kubectl apply -k sample4/
     kubectl get all -n test
    ```
- Sample 5: Organize K8S manifests in to a app specific structures with multiple manifests in each application specific directories
  ```
     kubectl apply -k sample4/
     kubectl get all -n test
    ```
- Sample 6: Change the image versions
  ```
     kubectl apply -k sample4/
     kubectl get all -n test

     kubectl describe deployment redis-db -n test | grep Image
     kubectl describe deployment nginx -n test | grep Image
    ```
- Sample 7: Change specific values of specific kubernetes entities with Patching. 
Patches are defined inline within the kustomization.yaml file
  ```
     kubectl apply -k sample7/
     kubectl get all -n test

     kubectl describe deployment nginx -n test | grep Name:
    ```

- Sample 8: Change specific values of specific kubernetes entities with Patching, and patches defined in separate files
  ```
     kubectl apply -k sample8/
     kubectl get all -n test

     kubectl describe deployment nginx -n test | grep Replicas:
    ```

- Sample 9: Change specific values of specific kubernetes entities with Patching, and patches defined in separate files
  ```
     kubectl apply -k sample8/
     kubectl get all -n test

     kubectl describe deployment nginx -n test | grep Replicas:
    ```

## Prerequisites
 
 - A running K8S cluster with Kubectl context set properly
 - K8S test namespace
    ```
     kubectl create namespace
    ```
