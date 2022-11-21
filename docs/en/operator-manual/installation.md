## Prerequisites

- Installed [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and [kubevela](https://kubevela.net/docs/installation/kubernetes#install-vela-cli) command-line tool.
- Have a [kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) file (default location is ~/.kube/config).



## Install for Kind

```bash
brew install kubevela
brew install kind
```

### Create a local cluster

```shell
echo "kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
    image: kindest/node:v1.22.15
" > kind-kiae.yaml
kind create cluster --name kiae --config kind-kiae.yaml
```

### Installation

```bash
vela addon registry add Kiae --type helm --endpoint=https://kiaedev.github.io/vela-addons
vela addon enable fluxcd
vela addon enable kiae
```