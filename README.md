# audito-maldito helm chart

![Version: 0.1.4](https://img.shields.io/badge/Version-0.1.4-informational?style=for-the-badge)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=for-the-badge)
![AppVersion: v0.0.1](https://img.shields.io/badge/AppVersion-v0.0.1-informational?style=for-the-badge)

This is a helm chart that deploys a [audito-maldito](https://github.com/metal-toolbox/audito-maldito) instance.

## Description

A Helm chart for deploying audito-maldito in Kubernetes provided
and maintained by your friends at Equinix Metal.

## Usage

Audito-maldito is deployed as a daemonset with two containers. One running the
actual audito-maldito workload, and another one outputting the audit logs.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| health.readiness.initialDelaySeconds | int | `30` |  |
| health.readiness.periodSeconds | int | `10` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/metal-toolbox/audito-maldito/audito-maldito"` |  |
| image.tag | string | `"v0.4.1"` |  |
| metrics.enabled | bool | `true` |  |
| priorityClassName | string | `""` |  |
| resources.limits.cpu | int | `1` |  |
| resources.limits.memory | string | `"512Mi"` |  |
| resources.requests.cpu | int | `1` |  |
| resources.requests.memory | string | `"512Mi"` |  |

## Development

### Prerequisites

- [helm](https://helm.sh/docs/intro/install/)
- [helm-docs](https://github.com/norwoodj/helm-docs)

### Testing

Ensure that the documentation is up to date before pushing a pull request:

```bash
helm-docs
```

### Releasing

There is a useful Makefile target that's useful to cut a release. So, simply do:

```bash
TAG=$RELEASE_VERSION make release
```

And the release will happen.

Note that this project follows the [Semantic Versioning scheme](https://semver.org/), so
make sure to follow it when cutting releases.

The `TAG` Makefile variable takes a release version without the `v` prefix. For example,
if you want to cut a release with version `v1.2.3`, you'd do:

```bash
TAG=1.2.3 make release
```
