# nginx sidecar proxy

This repo provides a minimal example of an nginx sidecar that can proxy an external service on localhost within the pod.

## Installation

```sh
kubectl apply -n some_namespace -f configmap.yaml
kubectl apply -n some_namespace -f deployment.yaml
```

## Testing

You can test out the proxy from within the pod by exec'ing in.

```sh
kubectl exec -n some_namespace -it deploy/nginx -- sh
```

Once inside, you can install and usee `wget`.

```sh
apt update
apt install wget
wget -O - http://localhost:5678/
```

After running this, you should see the contents of neverssl.com on stdout.
