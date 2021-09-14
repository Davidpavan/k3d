# k3d
#################
To create cluster
#################
k3d cluster create cluster-name
k3d cluster delete cluster-name

k3d cluster create --config k3d.yaml
k3d cluster list
docker ps

################################
Try to create k8s manifest files
################################
kubectl create deployment nginx --replicas=2 --image=nginx --dry-run=client -o yaml >k8s/nginx-deploy.yml
k create service clusterip nginx-service --tcp=8080:8080 --dry-run=client -o yaml >k8s/nginx-service.yml
k create 

k3d node list
k3d cluster list

k apply -f k8s/nginx-deploy.yml
k apply -f k8s/nginx-service.yml
k apply -f k8s/ingress.yml

k delete deployment/nginx
k delete svc/nginx-service
k delete ing/nginx-ingress

kubectl delete deployment --all

kubectl taint nodes k3d-k3d-cluster-agent-0 key1=value1:NoSchedule