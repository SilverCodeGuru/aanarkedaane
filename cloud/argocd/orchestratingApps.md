# orchestrating apps

## argocd Projects
- defualt if for demo
- projects are for multi-tenant situation with gaurd rails
- defines where resoruces can be deployed and from where source can be read 
- which resources can be deployed etc.

## propagation policies

- delete propogation plicy by default is background

- deployment owns replicaset and replicaset own pods. what happens on deletion of deployment

## Sync phase and hooks

presync phase - run presync hook jobs

sync phase - run jobs with sync hook, and apply application manifests

syncfail phase - jobs with syncfail hook are run

if success and healthy then post sync phase - run postsync hook jobs

postdelete, skip - other hooks

##