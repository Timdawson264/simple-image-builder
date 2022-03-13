# Installing

The pre built manifests will deploy the opeartator to the namespace `simple-image-builder-operator`

kubectl apply https://raw.githubusercontent.com/Timdawson264/simple-image-builder/main/rendered-manifest.yaml

# Example
Below is an example ImageBuild.

~~~
apiVersion: build.k8s.tdawson.co.nz/v1alpha1
kind: ImageBuild
metadata:
  name: hello-world
  namespace: default
spec:
  build:
    dockerfile: "Dockerfile"
    context: "/amd64/hello-world/"
    destination: "registry.registry.svc.cluster.local/workspace/stunnel:latest"
  git:
    repo: git@github.com:docker-library/hello-world.git
    branch: master
~~~

# Known Issues
Below is a list of unsupported features at this time.

- Authentication with docker registery not supported.
- Alternative sources:
 - https git
 - inline dockerfiles