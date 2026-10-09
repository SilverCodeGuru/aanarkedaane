# Fundamentals

operating system of cloud
bunch of vms that can communicate with each other
before there was ansible - very complicated.

It has a control plane - brain.

each VM is a worker node. worker node runs application.

intelleigent way to running container workloads at scale

it can also create nodes? surprise!!

distributing compute over nodes

## where to look

https://kubernetes.io/docs/reference/kubectl/generated/
https://kubernetes.io


pod is smallest elements in kubernetes.
its a collection of containers
simplest ones have just one container
k describe pod nginx 

and it shows containers in there.

pod also contains information about networking and storage

control plane is the api server and serves all commands you send using kubectl
components

- scheduler - decides which node to go to .. assign pods to nodes
- api server - listening on a port e.g. 6443
- etcd - brain

kubectl current context is stored in .kube/config file and has server

```
kapil@SLB-8GRK224:~/personal/src/trainings/kubernetes$ cat ~/.kube/config
apiVersion: v1
clusters:
- cluster:
    certificate-authority: /home/kapil/.minikube/ca.crt
    extensions:
    - extension:
        last-update: Fri, 02 Oct 2026 14:03:39 MDT
        provider: minikube.sigs.k8s.io
        version: v1.38.1
      name: cluster_info
    server: https://127.0.0.1:39451
  name: minikube
contexts:
- context:
    cluster: minikube
    extensions:
    - extension:
        last-update: Fri, 02 Oct 2026 14:03:39 MDT
        provider: minikube.sigs.k8s.io
        version: v1.38.1
      name: context_info
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
```

you can edit resources but dont.

k edit pod nginx

add new metadata

k run --dry-run=client

k apply -f nginx.yaml - declarative, idempotent, run again and again - creates, updates or does nothing

k create -f nginx.yaml - fails if resource exists

: set paste - paste with formatting from docs


k exec -it nginx -- /bin/bash

ctrl+d to exit
exit to exit
