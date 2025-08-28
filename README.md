# audito-maldito helm chart

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=for-the-badge)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=for-the-badge)
![AppVersion: v0.0.1](https://img.shields.io/badge/AppVersion-v0.0.1-informational?style=for-the-badge)

A Helm chart for deploying [audito-maldito][audito-maldito] in Kubernetes.
This chart is provided and maintained by your friends at Equinix Metal.

[audito-maldito]: https://github.com/metal-toolbox/audito-maldito

## Usage

audito-maldito is deployed as a [daemonset][daemonset]. This includes
several containers:

- `audito-maldito` - The containerized audito-maldito process. It reads from
  data sources using named pipes provided via a shared volume
- `rsyslog` - A containerized rsyslog process that reads log messages from
  OpenSSH daemon and other sources and writes them to named pipes.
  The named pipes are shared with audito-maldito via a shared volume
- `audittail` - A containerized Go program that reads audito-maldito's
  audit events and writes them to stdout

[daemonset]: https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| audittail.resources.limits.cpu | string | `"100m"` |  |
| audittail.resources.limits.memory | string | `"50Mi"` |  |
| audittail.resources.requests.cpu | string | `"100m"` |  |
| audittail.resources.requests.memory | string | `"25Mi"` |  |
| health.readiness.initialDelaySeconds | int | `30` |  |
| health.readiness.periodSeconds | int | `10` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/metal-toolbox/audito-maldito/audito-maldito"` |  |
| image.tag | string | `"v0.5.1"` |  |
| metrics.enabled | bool | `true` |  |
| priorityClassName | string | `""` |  |
| resources.limits.cpu | string | `"200m"` |  |
| resources.limits.memory | string | `"512Mi"` |  |
| resources.requests.cpu | string | `"200m"` |  |
| resources.requests.memory | string | `"256Mi"` |  |
| rsyslog.resources.limits.cpu | string | `"100m"` |  |
| rsyslog.resources.limits.memory | string | `"512Mi"` |  |
| rsyslog.resources.requests.cpu | string | `"100m"` |  |
| rsyslog.resources.requests.memory | string | `"256Mi"` |  |

## Development

### Prerequisites

- [helm](https://helm.sh/docs/intro/install/)

### Documentation

The helm documentation will automatically be re-generated when pushing up a pull request.

### Releasing

This chart uses [release-please](https://github.com/googleapis/release-please) to automate releases. [release-please](https://github.com/googleapis/release-please?tab=readme-ov-file#how-should-i-write-my-commits) assumes you are using [conventional commit messages](https://www.conventionalcommits.org/) to determine the next release version.
