# kustomize difference between patches and patchesJson6902

`$ kustomize build patchesJson6902` gets resources patch but `$ kustomize build patches` doesn't.
Is this intentional?

```
$ kustomize version
{Version:kustomize/v3.6.1 GitCommit:c97fa946d576eb6ed559f17f2ac43b3b5a8d5dbd BuildDate:2020-05-27T20:47:35Z GoOs:linux GoArch:amd64}

$ kustomize build patchesJson6902
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ${SERVICE_NAME}
spec:
  template:
    spec:
      containers:
      - image: ${DOCKER_IMAGE}
        name: ${SERVICE_NAME}
        resources:
          requests:
            cpu: 1m
            memory: 1Mi

$ kustomize build patches
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ${SERVICE_NAME}
spec:
  template:
    spec:
      containers:
      - image: ${DOCKER_IMAGE}
        name: ${SERVICE_NAME}
```
