## Setup Kubernetes Cluster
#### Install kubectl
    $ brew install kubectl

#### Install minikube  
    $ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.20.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
    $ brew install docker-machine-driver-xhyve
    $ sudo chown root:wheel /usr/local/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
    $ sudo chmod u+s /usr/local/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
    $ minikube start --memory=2048 --vm-driver=xhyve
    $ kubectl config get-contexts

#### Enable ingress  
    $ minikube addons enable ingress

#### Generate TLS  
    $ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /tmp/tls.key -out /tmp/tls.crt -subj "/CN=todoapp.local"
    $ kubectl create secret tls ingress-tls-secret --key /tmp/tls.key --cert /tmp/tls.crt --namespace=todo

#### Add domain to hosts file  
    $ echo "$(minikube ip) todoapp.local" | sudo tee --append /etc/hosts

## Deploy application  
    $ kubectl apply -R -f k8s/

[Try app out!](https://todoapp.local)
