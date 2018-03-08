# Kubernetes Sample

## Local setup with minikube
[Link](https://github.com/kubernetes/minikube)
```bash
# setup minikube
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

# start minikube
$ minikube start

# show config
$ cat ~/.kube/config

# setup kubectl
$ curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x kubectl
$ chmod +x ./kubectl
$ sudo mv ./kubectl /usr/local/bin/kubectl

```

## Run
```bash
# create deployment
$ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080

# expose deployment / create service
$ kubectl expose deployment hello-minikube --type=NodePort

# show url
$ minikube service hello-minikube --url

# minikube stop
$ minikube stop
```