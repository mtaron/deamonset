

https://gist.github.com/alexeldeib/f3517b9f166d8be4039ca5fbf89b9743
https://github.com/alexeldeib/azbench/blob/main/images/nsenter/entrypoint.sh
https://medium.com/@patnaikshekhar/initialize-your-aks-nodes-with-daemonsets-679fa81fd20e
https://github.com/patnaikshekhar/AKSNodeInstaller/blob/master/k8s/daemonset.yaml


az acr login -n docugami
docker build -t docugami.azurecr.io/nsenter .
docker push docugami.azurecr.io/nsenter
