# k8s-local

For bootstrapping my local k8s cluster running on my laptop.
This should 100% not be used outside of a local laptop environment.

## Running
Pass requests hitting http://local.projectcontour.io:8888 to my local Kind cluster
setup in podman (with the contour-gateway defined in helm-base)
```bash
kubectl -n projectcontour port-forward service/envoy-contour "8888:80"
```

### Argo
Will install everything via the application-set defined in `application-sets/base`.
This is not auto-created with Argo yet.

```bash
curl http://local.projectcontour.io:8888/argo
```

### External Secrets
Will be setup to pull from the Hashicorp vault

### Vault
**N.B.** Vault can't run on a subpath at the moment so has to take the root path
```bash
curl http://local.projectcontour.io:8888/
```
Either set vault up with the ui or by following steps [here](https://developer.hashicorp.com/vault/tutorials/kubernetes/kubernetes-minikube-raft).
Note: that this setup is not HA and if you like your laptop, nor should it be.
