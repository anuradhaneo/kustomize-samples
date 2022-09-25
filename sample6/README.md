This sample shows how you want to change/override the Docker image or the image version.

If you want to change the image version use something like below in the kustomization.yaml
```
    images:
    - name: nginx
        newTag: stable
```
Above will change the image version from 'latest' to 'stable'

If you want to change the image completely along with the version use something like below in the kustomization.yaml
```
    images:
    - name: nginx
        newName: bitnami/nginx
        newTag: 1.22.0
```

Above will change and deploy the official nginx image to 'bitnami/nginx:1.22.0' 
