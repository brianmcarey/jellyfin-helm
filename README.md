# Archived 2024-11-12

The repository has been archived. 

See the helm chart provided by the Jellyfin project - https://github.com/jellyfin/jellyfin-helm

This is a helm chart for [Jellyfin](https://github.com/jellyfin/jellyfin/)

## Prerequisites

- Kubernetes 1.19+
- Helm 3+

## TL;DR;

```shell
$ git clone https://github.com/brianmcarey/jellyfin-helm.git
$ helm install ./jellyfin-helm
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
git clone https://github.com/brianmcarey/jellyfin-helm.git
helm install  my-release ./jellyfin-helm
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Jellyfin chart and their default values.

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `image.repository`         | Image repository | `docker.io/jellyfin/jellyfin` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/jellyfin/jellyfin/tags/).| `latest`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `enableDLNA`		  | Enable DLNA for jellyfin | `false` |
| `Service.type`          | Kubernetes service type for the jellyfin GUI | `ClusterIP` |
| `Service.port`          | Kubernetes port where the jellyfin GUI is exposed| `8096` |
| `Service.annotations`   | Service annotations for the jellyfin GUI | `{}` |
| `Service.labels`        | Custom labels | `{}` |
| `Service.loadBalancerIP` | Loadbalance IP for the jellyfin GUI | `{}` |
| `Service.loadBalancerSourceRanges` | List of IP CIDRs allowed access to load balancer (if supported)      | None
| `ingress.enabled`              | Enables Ingress | `false` |
| `ingress.annotations`          | Ingress annotations | `{}` |
| `ingress.labels`               | Custom labels                       | `{}`
| `ingress.path`                 | Ingress path | `/` |
| `ingress.hosts`                | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`                  | Ingress TLS configuration | `[]` |
| `persistence.config.enabled`      | Use persistent volume to store configuration data | `false` |
| `persistence.config.size`         | Size of persistent volume claim | `1Gi` |
| `persistence.config.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.config.storageClass` | Type of persistent volume claim | `-` |
| `persistence.config.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.media.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.media.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.media.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.media.storageClass` | Type of persistent volume claim | `-` |
| `persistence.media.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.extraExistingClaimMounts`  | Optionally add multiple existing claims | `[]` |
| `resources`                | CPU/Memory resource requests/limits | `{}` |
| `nodeSelector`             | Node labels for pod assignment | `{}` |
| `tolerations`              | Toleration labels for pod assignment | `[]` |
| `affinity`                 | Affinity settings for pod assignment | `{}` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Read through the [values.yaml](values.yaml) file. It has several suggested values.
