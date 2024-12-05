# Custom Kubernetes Controller Helm Chart

This Helm chart deploys a custom Kubernetes controller that extends the control plane using aggregated APIs.

## Features

- Custom Resource Definition (CRD) for managing custom resources
- Configurable controller settings through Helm values
- RBAC configuration for secure operation
- Leader election support for high availability
- Resource management and scaling options

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+

## Installation

1. Clone this repository:
```bash
git clone [your-repository-url]
```

2. Update the values in `values.yaml` with your configuration:
```yaml
image:
  repository: your-registry/custom-controller
  tag: your-version
```

3. Install the chart:
```bash
helm install custom-controller ./custom-controller
```

## Configuration

The following table lists the configurable parameters of the custom-controller chart and their default values:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of controller replicas | `1` |
| `image.repository` | Controller image repository | `custom-controller` |
| `image.tag` | Controller image tag | `latest` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `controller.logLevel` | Controller log level | `info` |
| `controller.workers` | Number of worker threads | `2` |
| `controller.resyncPeriod` | Resource resync period in seconds | `30` |
| `resources.limits.cpu` | CPU resource limits | `500m` |
| `resources.limits.memory` | Memory resource limits | `512Mi` |
| `resources.requests.cpu` | CPU resource requests | `250m` |
| `resources.requests.memory` | Memory resource requests | `256Mi` |

## Custom Resource Definition

The chart includes a CRD for managing custom resources. Example custom resource:

```yaml
apiVersion: custom.k8s.io/v1
kind: CustomResource
metadata:
  name: example-resource
spec:
  schedule: "*/5 * * * *"
  configuration:
    key: value
```

## License

MIT License
