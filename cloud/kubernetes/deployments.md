# deployments

how a deplpoyment know which pods it manages? using selector matchlabels

```
  selector:
    matchLabels:
      app: my-dep
```

replicaset is internal - user should never manage it

it is managed by deployment

strategy - recreate - delete all and then start creating new ones

rollingupdate
watch -n 1 "kubectl get pods"
every second run kgp


crashloopbackoff
runcontainererror

prevent us from destroying app completely

## namespace

grouping of namespace scoped resources. some resources are cluster scopes e.g. nodes and these cant be grouped at namespace level.

ns is shortcut

k get ns

default namespace

how to set your namespace as current namespace else you need to type --namespace=your_ns in all commands

k get pods --namespace=your_ns

k config set-context --current --namespace=your_ns

when you run a pod, it gets created in the default namespace by default. if you switch want it to be created in your namespace, again add --namespace=your_ns at the end

you delete a namespace, all resources under it get deleted.



