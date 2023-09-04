# operator-sdk bug

Sample app to demo a Red Hat `operator-sdk` bug on OpenShift.

Bug Report on Upstream: https://github.com/operator-framework/operator-sdk/issues/6557

## Environment

```
Openshift Version: OpenShift v4.12.25
```
```
Kubectl Version: Client Version: v1.28.0
                 Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3
                 Server Version: v1.25.11+1485cc9
                 WARNING: version difference between client (1.28) and server (1.25) exceeds the supported minor version skew of +/-1
```
```
Operator SDK Version: operator-sdk version: "v1.31.0", commit: "e67da35ef4fff3e471a208904b2a142b27ae32b1", kubernetes version: "1.26.0", go version: "go1.19.11", GOOS: "linux", GOARCH: "amd64"
```

## Summary

This is a Sample Hello World Helm Chart with a Deployment which has dependencies on grafana chart. 
While initializing a new project using `operator-sdk init` it fails with following error.

```bash
$ operator-sdk init \ 
  --project-name=hello-world-operator --plugins=helm --domain=dev \
  --helm-chart=./helm/hello-world
  
Writing kustomize manifests for you to edit...
Creating the API:
$ operator-sdk create api --helm-chart ./helm/hello-world
Writing kustomize manifests for you to edit...

Error: failed to create API: unable to scaffold with "base.helm.sdk.operatorframework.io/v1": failed to fetch chart dependencies: directory /home/user/Projects/operator-sdk-bug/helm-charts/hello-world/charts/grafana not found
...
...
...
...
FATA[0000] failed to initialize project: unable to run post-scaffold tasks of "base.helm.sdk.operatorframework.io/v1": exit status 1 
```
