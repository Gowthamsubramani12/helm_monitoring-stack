# prom-stack-chart

A Helm chart for a complete Prometheus + Grafana monitoring stack on Kubernetes.

## Components

This chart deploys the following components:

- **Prometheus Server**: StatefulSet with Persistent Volume.
- **Alertmanager**: Deployment for handling alerts.
- **Node Exporter**: DaemonSet for node metrics.
- **Kube State Metrics**: Deployment for Kubernetes object metrics.
- **Pushgateway**: Deployment for ephemeral jobs.
- **Grafana**: Deployment for visualization, with auto-provisioned Prometheus datasource.

## Installation

```bash
helm install prom-stack ./prom-stack-chart
```

## Configuration

The following table lists the configurable parameters of the chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `prometheus.image.repository` | Prometheus image repository | `prom/prometheus` |
| `prometheus.image.tag` | Prometheus image tag | `v2.45.0` |
| `prometheus.persistence.enabled` | Enable persistence for Prometheus | `true` |
| `prometheus.persistence.size` | Size of the PVC | `10Gi` |
| `alertmanager.image.repository` | Alertmanager image repository | `prom/alertmanager` |
| `grafana.adminUser` | Grafana admin username | `admin` |
| `grafana.adminPassword` | Grafana admin password | `admin` |
| `grafana.ingress.enabled` | Enable Ingress for Grafana | `false` |

See `values.yaml` for the full list of configuration options.

## Accessing Grafana

1. Port-forward the Grafana service:
   ```bash
   kubectl port-forward svc/prom-stack-prom-stack-chart-grafana 3000:80
   ```
2. Open your browser at `http://localhost:3000`.
3. Login with `admin` / `admin` (or your configured credentials).
