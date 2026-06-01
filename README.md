# kubernetes-microservice-deployment

Kubernetes deployment project for a portfolio website, using raw manifests and a bonus Helm chart.

## Project Structure

```text
.
├── app/
│   ├── Dockerfile
│   ├── index.html
│   └── nginx.conf
├── manifests/
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── ingress.yaml
│   ├── secret.yaml
│   └── service.yaml
└── helm/
    └── portfolio-website/
        ├── Chart.yaml
        ├── values.yaml
        └── templates/
```

## Build And Push Image

Replace `your-dockerhub-user` with your registry username.

```bash
docker build -t your-dockerhub-user/portfolio-website:1.0.0 ./app
docker push your-dockerhub-user/portfolio-website:1.0.0
```

Update the image in `manifests/deployment.yaml` or override it during Helm install.

## Deploy With Kubernetes Manifests

```bash
kubectl apply -f manifests/
kubectl get pods,svc,ingress -n portfolio
```

For local testing with Minikube:

```bash
minikube addons enable ingress
kubectl apply -f manifests/
```

Add this host entry if needed:

```text
<INGRESS_IP> portfolio.local
```

Then open:

```text
http://portfolio.local
```

## Deploy With Helm

```bash
helm install portfolio ./helm/portfolio-website \
  --namespace portfolio \
  --create-namespace \
  --set image.repository=your-dockerhub-user/portfolio-website \
  --set image.tag=1.0.0
```

Upgrade after changes:

```bash
helm upgrade portfolio ./helm/portfolio-website -n portfolio
```

Uninstall:

```bash
helm uninstall portfolio -n portfolio
```

## Included Kubernetes Objects

- Deployment
- Service
- ConfigMap
- Secret
- Ingress
- Helm chart

