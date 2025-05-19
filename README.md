## Get repo

Assumed that `helm`, `git`, etc. are already installed.

```bash
git clone https://github.com/emrahcom/jitsi-helm-case-1.git

cd jitsi-helm-case-1
git pull
```

## Dependencies

```bash
helm dependency update
```

## myvalues.yaml

[myvalues.yaml](myvalues.yaml) is created using only the critical values from
the default `values.yaml` of `jitsi-meet` chart.

To show the default `values.yaml`:

```bash
helm show values charts/jitsi-meet-1.4.1.tgz
```

A few lines from the custom [myvalues.yaml](myvalues.yaml):

```yaml
jitsi:
  publicURL: "meet.minikube.loc"

  web:
    replicaCount: 1
    image:
      repository: jitsi/web
      tag: "stable-10184"
```

## Install

```bash
helm install myjitsi . -f myvalues.yaml

kubectl get pods
kubectl get ingress
```

## Uninstall

```bash
helm uninstall myjitsi
```
