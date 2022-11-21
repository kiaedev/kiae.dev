## Prerequisites

- Kubernetes 1.22+
- KubeVela 1.5+
- Istio 1.15+
- Kpack 0.7+
- Loki 2.6+
- Helm 3+

## Install for Kind

### Kind

```bash
kind create cluster --name kiae --config samples/kind/config.yml
```

### Vela

```bash
vela install

vela addon registry add Kiae --type helm --endpoint=https://kiaedev.github.io/vela-addons
vela addon enable fluxcd
vela addon enable kiae
```