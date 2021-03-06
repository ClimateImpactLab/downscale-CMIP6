# ingress-nginx
This component is a basic cluster ingress.

## Pre-deployment
Be sure the `ingress-nginx` Namespace exists on the cluster.
Create the Namespace with
```bash
kubectl create namespace "ingress-nginx"
```

## Deploy (`argocd`)

You can deploy this in a dev environment with `argocd` from the CLI with

```bash
argocd app create ingress-nginx \
    --repo https://github.com/ClimateImpactLab/downscaleCMIP6 \
    --path infrastructure/kubernetes/ingress-nginx \
    --values values.yaml \
    --dest-server https://kubernetes.default.svc \
    --dest-namespace ingress-nginx \
    --sync-policy automated \
    --auto-prune \
    --port-forward-namespace argocd
```
