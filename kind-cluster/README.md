``` bash

./install_kind.sh  
kind create cluster --name=rk-cluster --config=config.yml
kubectl cluster-info --context kind-rk-cluster
kubectl get nodes
kubectl get ns
kubectl get pods
kubectl get pods -n kube-system
kubectl run nginx --image=nginx
kubectl delete pod nginx
kubectl create ns nginx
kubectl run nginx --image=nginx -n nginx
create namespace.yml and pod.yml
kubectl apply -f namespace.yml
kubectl apply -f pod.yml
kubectl exec -it nginx-pod -n nginx -- bash
kubectl describe pod/nginx-pod -n nginx
create deployment.yml
kubectl apply -f deployment.yml
kubectl get pods -n nginx
kubectl get deployments -n nginx
kubectl scale deployments/nginx-deployment -n nginx --replicas=5
kubectl get pods -n nginx
create replicasets.yml
kubectl apply -f replicasets.yml
kubectl get replicasets -n nginx
kubectl get pods -n nginx
kubectl get pods -n nginx -o wide
kubectl apply -f daemonsets.yml
kubectl get pods -n nginx -o wide
kubectl apply -f job.yml
kubectl get jobs -n nginx
kubectl get pods -n nginx
kubectl delete -f daemonsets.yml
kubectl delete -f job.yml
kubectl get pods -n nginx
kubectl logs pod/demo-job-xws6p -n nginx
kubectl apply -f cronjob.yml
kubectl get pods -n nginx
