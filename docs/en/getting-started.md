## Prerequisites

- Installed [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and [kubevela](https://kubevela.net/docs/installation/kubernetes#install-vela-cli) command-line tool.
- Have a [kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) file (default location is ~/.kube/config).

## 1. Install the command-line tools

```bash
brew update
brew install kind
brew install kubevela
```

## 2. Create a local cluster

```shell
echo "kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
    image: kindest/node:v1.22.15
" > kind-kiae.yaml
kind create cluster --name kiae --config kind-kiae.yaml
```

## 3. Install the kubevela-core

```bash
vela install
```

## 4. Install the Kiae

```bash
vela addon registry add Kiae --type helm --endpoint=https://kiaedev.github.io/vela-addons
vela addon enable fluxcd onlyHelmComponents=true
vela addon enable kiae
```

## 5. Access the Kiae

By default, the Kiae server is not exposed with an external IP. To access the Kiae, choose one of the following techniques to expose the Kiae server:

### Service Type Load Balancer

Change the kiae service type to LoadBalancer:

```bash
kubectl patch svc kiae -n kiae-system -p '{"spec": {"type": "LoadBalancer"}}'
```

### IngressGateway

Follow the ingressgateway documentation on how to configure Kiae with ingressgateway.

### Port Forwarding

Kubectl port-forwarding can also be used to connect to the API server without exposing the service.

```bash
kubectl port-forward svc/kiae -n kiae-system 8081:8081
```

The Kiae can then be accessed using [http://localhost:8081](http://localhost:8081)

## 6. Login the Kiae

For the first login, you must login the with the administrator account. The default username and password is below:

- Username: admin@example.com
- Password: password

## 7. Configure the GitProvider

You must [configure the GitProvider](/operator-manual/git-provider/) to support the developer get the source repository.


## 8. Configure the ImageRegistry

You must [configure the ImageRegistry](/operator-manual/image-registry/) to support the ImageBuilder save image.

## 9. Configure the ImageBuilder

You must [configure the ImageBuilder](/operator-manual/image-builder/) to support the developer build the source repository
