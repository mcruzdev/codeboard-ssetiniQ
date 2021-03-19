
# ssetniQ

## Codeboard

### Pre-requisitos

- [Docker](https://www.docker.com/)
- [Kubernetes](https://kubernetes.io/)
- [kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)

### Criando o nosso cluster Kubernetes

```
kind create cluster --name ssetniq
```

### Instalando o Rancher
```
$ docker run -d --restart=unless-stopped -p 80:80 -p 443:443 --privileged rancher/rancher:latest
```

### Instalando o Dynatrace

```
$ kubectl create namespace dynatrace
$ kubectl apply -f https://github.com/Dynatrace/dynatrace-oneagent-operator/releases/latest/download/kubernetes.yaml
$ kubectl -n dynatrace logs -f deployment/dynatrace-oneagent-operator
```

Configuração:
```
kubectl -n dynatrace create secret generic oneagent --from-literal="apiToken=API_TOKEN" --from-literal="paasToken=PAAS_TOKEN"
```