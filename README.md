# Talahon Tech Static Website

This repository contains a simple static website served using Nginx in a Docker container and deployed using Helm.

## Project Structure
```
.
├── Dockerfile           # Docker image definition
├── index.html          # Static website content
├── Chart.yaml          # Helm chart definition
├── values.yaml         # Default Helm values
└── templates/          # Helm templates
    ├── deployment.yaml
    └── service.yaml
```

## Building the Docker Image

```bash
docker build -t talahon/static-site:latest .
docker push talahon/static-site:latest
```

## Installing the Helm Chart

```bash
helm install my-website .
```

## Configuration

The following table lists the configurable parameters of the chart and their default values:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `talahon/static-site` |
| `image.tag` | Image tag | `latest` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.port` | Kubernetes service port | `80` |

## Accessing the Website

After installing the chart, you can access the website by port-forwarding the service:

```bash
kubectl port-forward svc/my-website 8080:80
```

Then visit http://localhost:8080 in your browser. 