# k8s-local

For bootstrapping my local k8s cluster running on my laptop.
This should 100% not be used outside of a local laptop environment.

## Running
Pass requests hitting http:local.projectcontour.io:8888 to my local Kind cluster
setup in podman (with the contour-gateway defined in helm-base)
```bash
kubectl -n projectcontour port-forward service/envoy-contour "8888:80"
```

