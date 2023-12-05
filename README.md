# demo-cicd
OpenShift Pipelines + GitOps + ACS

## Use Cases

### Building app with OpenShift Pipelines (Tekton) using S2I

```
oc apply -f use-cases/build-s2i/Pipeline/namespace.yaml
oc apply -f use-cases/build-s2i/Pipeline/quarkus-build-pi.yaml
oc create -f use-cases/build-s2i/PipelineRun/quarkus-build-pr.yaml
```

### Building app with OpenShift Pipelines (Tekton) using S2I and deploying with OpenShift GitOps (ArgoCD)

```
oc apply -f use-cases/deploy-with-argocd/Rolebindings/
oc apply -f use-cases/deploy-with-argocd/Pipeline/quarkus-build-and-deploy-pi.yaml
oc create -f use-cases/deploy-with-argocd/PipelineRun/quarkus-build-and-deploy-pr.yaml
```

### Building app with OpenShift Pipelines (Tekton) checking vulnerabilities with RH ACM and deploying with OpenShift GitOps (ArgoCD)

```
oc apply -f use-cases/devsecops-with-rhacm/Task/
oc apply -f use-cases/devsecops-with-rhacm/Pipeline/quarkus-devsecops-v1-pi.yaml
oc create -f use-cases/devsecops-with-rhacm/PipelineRun/quarkus-devsecops-v1-pr.yaml
```

*Fixing sec vulnerability*:

```
oc apply -f use-cases/devsecops-with-rhacm/Task/
oc apply -f use-cases/devsecops-with-rhacm/Pipeline/quarkus-devsecops-v2-pi.yaml
oc create -f use-cases/devsecops-with-rhacm/PipelineRun/quarkus-devsecops-v2-pr.yaml
```