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
kubectl apply -f persistentvolume.yml
kubectl get pv
kubectl apply -f persistentvolumeclaim.yml
kubectl get pv
kubectl apply -f persistentvolume.yml
kubectl apply -f persistentvolumeclaim.yml
kubectl get pv -n nginx
kubectl get pods -n nginx
kubectl get pods -n nginx -o wide
kubectl get nodes
kubectl apply -f service.yml
kubectl get all -n nginx
sudo -E kubectl port-forward service/nginx-service -n nginx 81:80 --address=0.0.0.0
#create ingress controller
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
kubectl get pods -n ingress-nginx
kubectl get pods -n ingress-nginx
kubectl get ns


kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.2/deploy/static/provider/kind/deploy.yaml
kubectl -n ingress-nginx patch deployment ingress-nginx-controller \
--type=json \  -p='[{"op":"add","path":"/spec/template/spec/containers/0/args/-","value":"--enable-admission-webhook=false"}]'
kubectl rollout restart deployment ingress-nginx-controller -n ingress-nginx
kubectl get pods -n ingress-nginx
kubectl port-forward service/ingress-nginx-controller -n ingress-nginx 8081:80 --address=0.0.0.0
kubectl apply -f configmap.yml
kubectl apply -f statefulset.yml
kubectl apply -f secret.yml
kubectl get pods -n  mysql
kubectl taint node rk-cluster-worker2 prod=true:NoSchedule
kubectl taint node rk-cluster-worker2 prod=true:NoSchedule-

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.5.0/components.yaml

kubectl -n kube-system edit deployment metrics-server

Add the security bypass to deployment under container.args
- --kubelet-insecure-tls
- --kubelet-preferred-address-types=InternalIP,Hostname,ExternalIP

kubectl -n kube-system rollout restart deployment metrics-server
kubectl get pods -n kube-system
kubectl top nodes
kubectl top pod -n nginx
kubectl top pod -n mysql
#HPA
kubectl scale deployment apache-deployment -n apache --replicas=3
kubectl run -it load-generator --image=busybox -n apache -- /bin/sh
run - while true; do wget -q -O- http://apache-service.default.svc.cluster.local; done

Now from other shell
kubectl get pods -n apache


cd apache;git clone https://github.com/kubernetes/autoscaler.git
cd autoscaler/vertical-pod-autoscaler/
./hack/vpa-up.sh
kubectl apply -f vpa.yml
kubectl delete horizontalpodautoscaler.autoscaling/apache-hpa -n apache
kubectl get vpa -n apache
kubectl run -it load-generator --image=busybox -n apache -- /bin/sh
run - while true; do wget -q -O- http://apache-service.apache.svc.cluster.local; done

kubectl top pod -n apache