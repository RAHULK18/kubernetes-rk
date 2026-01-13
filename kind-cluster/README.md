./install_kind.sh  
kind create cluster --name=rk-cluster --config=config.yml
kubectl cluster-info --context kind-rk-cluster
kubectl get nodes
