# portal-chart

Helm chart to deploy `monochrome-portal-ui` on Kubernetes.

## What it deploys

A Deployment and a ClusterIP Service for the portal UI, built from the image
`application/portal/portal-mirror-ui` under the configured registry.

## Values

| File | Purpose |
|---|---|
| `base.values.yaml` | Defaults shared across all environments |
| `lcl.values.yaml` | Local Kubernetes cluster (pik8s.internal) overrides |
| `snbx.values.yaml` | Sandbox GKE environment overrides |

There is no plain `values.yaml`. Always pass `base` plus exactly one environment file, `helm lint`
included: a bare `helm lint .` fails with no default values to fall back on.

## Local usage

```bash
# Lint
helm lint . -f base.values.yaml -f lcl.values.yaml

# Install (lcl)
helm install portal-chart . -f base.values.yaml -f lcl.values.yaml

# Install (snbx)
helm install portal-chart . -f base.values.yaml -f snbx.values.yaml
```

## License

[Elastic License 2.0](./LICENSE) — source-available; not OSI open source.
