This example shows how multiple K8S manifest files are linked together to form a single unit of configuration script.
In comparison to the sample-4, here there are more K8S manifests in each directory structre. In this case it is not easy to link all the files in different directories (db and lb in this sample) where there can be considerable number of yaml files.

In this case separate kustomization.yaml files will be stored within each directory. Main kustomization.yaml will automatically detect them while you only have to specify the directoriy paths from then main kustomization.yaml

> Note: 'test' namespace must pre-exist

To test run the below command
```
 kubectl apply -k sample5/
```
or 
```
 kustomize build sample5/ | kubectl apply -f -
```

above commands will output the below details immediately
```
  service/nginx created
  service/redis-db created
  deployment.apps/nginx-deployment created
  deployment.apps/redis-db created
```