# Networking in kubernetes

- each pod has a IP
- implemented using CNI plugin. each containter has NIC - has network connectivity.

- pod can have many containers

```
k port-forward deploymemts/pod-id 9000

k expose deployment my-deployment --port 8080

k port-forward services/mealie 9000

minikube tunnel
```

## services

a service offers consistent addresss to access a set of pods

clusterIP - cluster wide IP address for service.

nodeIP - avoid. exposes a port on each node allowing direct access to service through node's IP address.

LoadBalancer - gets an external IP

doesnt work with minikube. externalIP is for cloud providers. will work on rancher desktop.

minikube tunnel command will get you the externalIP but it is localhost 127.0.0.1

point is once the service is of type loadbalancer, you dont need to port forward.

your service is exposed outside your cluster automatically.



## Ingress

fully qualified domain name

urls are routed through ingress using route/routing rules



