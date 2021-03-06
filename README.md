# Minikube
sudo -i

curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
chmod +x minikube \
mv ./minikube /usr/bin/minikube 


curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
chmod +x ./kubectl \
mv ./kubectl /usr/bin/kubectl 


minikube start --vm-driver=none 
# to create pod/deployment
kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080 \ 
# to crate service/ to exposed
# specify the any port or it will take the default port
kubectl expose deployment hello-minikube --type=NodePort \
curl $(minikube service hello-minikube --url) \
# find the running pods
kubectl get pod 
# find the deployments
kubectl get deployment 
# to find the services
kubectl get svc

kubectl get nodes \
# it will give the service details 
curl $(minikube service hello-minikube --url) \

kubectl delete services hello-minikube \
kubectl delete deployment hello-minikube \
minikube stop 


minikube delete \
rm -rf ~/.minikube

# important references
`https://kubernetes.io/docs/concepts/workloads/controllers/deployment/`
 create the nginx-deployment.yaml from above site
`https://kubernetes.io/docs/concepts/services-networking/`
`https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/`

# steps to create deployment file and service file , execute and check
Create doployment.yaml file 
 sudo kubectl create -f nginx-deployment.yaml
   sudo kubectl get pod
   sudo kubectl get deployment
 Create service.yaml file 
 sudo kubectl create -f   nginx-svc.yaml
  sudo kubectl get pod
   sudo kubectl get deployment
   sudo kubectl get svc
   To connect the service internally 
   
   curl $(minikube service nginx-svc --url)

nginx-svc.yaml
to check
curl $(minikube service nginx-svc --url)


#------------------------
https://github.com/kubernetes/kubernetes/blob/master/cluster/addons/addon-manager/namespace.yaml
-------------commands---------------
https://kubernetes.io/docs/reference/kubectl/cheatsheet/

https://www.blazemeter.com/blog/how-to-setup-scalable-jenkins-on-top-of-a-kubernetes-cluster
