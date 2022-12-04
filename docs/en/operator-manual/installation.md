## Prerequisites

- Installed [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and [kubevela](https://kubevela.net/docs/installation/kubernetes#install-vela-cli) command-line tool.
- Have a [kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) file (default location is ~/.kube/config).

## Installation steps

1.Install the kubevela-core and kiae addons

```bash
vela install
vela addon registry add Kiae --type helm --endpoint=https://kiaedev.github.io/vela-addons
vela addon enable kiae
```

2.Install the Kiae

```bash
helm repo add kiaedev https://kiaedev.github.io/helm-charts
helm repo update
helm install -n kiae-system --create-namespace kiae kiaedev/kiae
```

3.(Optional) Install with configuration

```bash
helm install -n kiae-system --create-namespace kiae kiaedev/kiae --set config.server.url=http://kiae.example.com
```

## Verifying the installation

Status of the installation can be verified using Helm:

```bash
helm status kiae -n kiae-system
```

## Updating your Kiae configuration

You can provide override settings specific to any Kiae Helm chart used above and follow the Helm upgrade workflow to customize your Kiae installation. The available configurable options can be found by using `helm show values kiaedev/<chart>`; for example `helm show values kiaedev/kiae`.

```bash
echo 'config:
  debug: true
  server:
    port: 8081
    url: http://kiae.example.com
  dex:
    adminEmail: "admin@example.com"
    # bcrypt hash of the string "password": $(echo password | htpasswd -BinC 10 admin | cut -d: -f2)
    adminPasswd: "$2a$10$2b2cU8CPhOTaGrs1HRQuAueS7JTT5ZHsHSzYiFPm1leZck7Mc8T4W"
' > values.yaml
helm upgrade -n kiae-system kiae kiaedev/kiae -f values.yaml
```

## Uninstall

```bash
helm delete kiae -n kiae-system
vela addon disable kiae
vela uninstall
```
