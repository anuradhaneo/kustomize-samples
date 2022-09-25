# kustomize-samples

Some sample Kubernetes projects using Kustomize

## Samples Provided

- Sample1 : Simple kustomization of a nginx deployment that adds a label

- Sample2 : Like similar to Sample1, adds few more additional common transformers like namespace and a prefix to the deployment

- Sample 3 : Introduces Strategic-Merge patch that changes the replica count of the nginx deployments and also increases the memory resource allocations




## Prerequisites
 
 - K8S test namespace
    ```
     kubectl create namespace
    ```
