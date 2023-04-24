# deamonset to upgrade/downgrade Linux kernel on AKS

## Build and push nsenter container

```
az acr login -n docugami
docker build -t docugami.azurecr.io/nsenter .
docker push docugami.azurecr.io/nsenter
```

## Add gpu-operator

(To make sure it doesn't conflict with this deamonset.)

```
helm repo add nvidia https://helm.ngc.nvidia.com/nvidia && helm repo update
helm upgrade \
    --values gpu-operator.yaml \
    --install \
    --create-namespace \
    --namespace gpu-operator \
    --disable-openapi-validation \
    --version 23.3.1 \
    gpu-operator nvidia/gpu-operator
```

## Resources
https://gist.github.com/alexeldeib/f3517b9f166d8be4039ca5fbf89b9743
https://github.com/alexeldeib/azbench/blob/main/images/nsenter/entrypoint.sh
https://medium.com/@patnaikshekhar/initialize-your-aks-nodes-with-daemonsets-679fa81fd20e
https://github.com/patnaikshekhar/AKSNodeInstaller/blob/master/k8s/daemonset.yaml
https://unix.stackexchange.com/questions/198003/set-the-default-kernel-in-grub
https://kubernetes.io/docs/reference/kubectl/#in-cluster-authentication-and-namespace-overrides
