### Swagger deployment



For the Kubernetes deployment first of all, the istio setup must be running

```bash
git clone <link-to-repo>
cd swagger-GH
```
To set up the swagger with the keycloak api we need to apply the configmap

```bash
kubectl apply -f YAMLs/001_keycloak-api-configmap.yaml
```

Then apply the swagger deployment with the nuimber of replicas needed

```bash
kubectl apply -f YAMLs/002_swagger-deployment.yaml
```

To set up the service and the virtual service for Istio

```bash
kubectl apply -f YAMLs/003_swagger-service.yaml
kubectl apply -f YAMLs/004_swagger-vs.yaml
```

