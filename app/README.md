# CaaS PoC Fujitsu demo app

A demo app that can be deployd to a Kubernetes cluster. It displays a message, and also namespace, pod, node and image details.

## Paths

| Method | Path | Description |
| -------| ---- | ----------- |
| GET    | /    | Displays message, pod and node details |
| GET    | /generate-cpu-load    | generate cpu load for autoscaler |

## Configuration

The application can be configured via the following environment variables.

| Env | Required | Default Value | Description |
| --- | -------- | ------------- | ----------- |
| PORT | No | 8080 | The port that the app listens on. |
| MESSAGE | No | "CaaS PoC Fujitsu!" | The message displayed by the app. |
| KUBERNETES_NAMESPACE | Yes | "-" | The Kubernetes namespace that the app has been deployed to. |
| KUBERNETES_POD_NAME | Yes | hostname | The name of the Kubernetes pod that the app is deployed into. |
| KUBERNETES_NODE_NAME | Yes | "-" | The name of the Kubernetes node that the app is deployed on. |
| CONTAINER_IMAGE | Yes | "caas-poc-fujitsu:$(cat package.json \| jq -r .version)" | The name and tag of the container image running the app. |

The application relies on the following files for configuration and operational information.

| File | Required | Information | Description |
| ---- | -------- | ----------- | ----------- |
| package.json | Yes | `.version` | The release version is used when the CONTAINER_IMAGE env is not provided. |
| info.json | Yes | `.containerImageArch` | The container image architecture is used for display. This file will be overwritten in future versions as part of the container image build process when multi-arch images are supported. |
