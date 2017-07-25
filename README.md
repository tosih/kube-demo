## Setup Kubernetes Cluster
* Install kubectl
```$ brew install kubectl```
* Install minikube
```
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.20.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
$ brew install docker-machine-driver-xhyve
$ sudo chown root:wheel /usr/local/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
$ sudo chmod u+s /usr/local/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
$ minikube start --memory=2048 --vm-driver=xhyve
$ kubectl config get-contexts
```
* Enable ingress
```$ minikube addons enable ingress```

## Deploy application
```$ kubectl apply -f -R k8s```

## Try app out!