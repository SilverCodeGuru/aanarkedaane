# argocd compoenents

argocd lives in a separate namespace from application

## API Server

## Repository Server

local cache
generates manifests
talk to git repository

## Application controller

argocd-redis - cache manifests
dex-server - for identity management using smal and oidc
applicationset-controller - applications at scale

Application CRD

application custom resource definition

project - default project

sync policy
- prune
- selfheal

Application CR (custom resource) only understood by the Argo CD controllers
Kubernetes manifest 


CRD: custom resource definition
