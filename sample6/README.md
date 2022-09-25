If you want to change the image completely use something like below in the kustomization.yaml

images:
  - name: nginx
    newName: bitnami/nginx
    newTag: 1.22.0