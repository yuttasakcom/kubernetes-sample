# Kubernetes Sample

## Local setup with minikube
```bash
# link
https://github.com/kubernetes/minikube

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

## Example
```bash
# create deployment
$ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080

# expose deployment / create service
$ kubectl expose deployment hello-minikube --type=NodePort

# show url
$ minikube service hello-minikube --url

# delete deployment
$ kubectl delete deployment hello-minikube

# minikube stop
$ minikube stop
```

## Pod
```
===== Useful Commands =====
kubectl get pod
kubectl describe pod <pod>
kubectl expose pod <pod> --port=8080 --name=frontend
kubectl port-forward <pod> 8080:8080
kubectl attach <pod> -i
kubectl exec <pod> -- command
kubectl label pods <pod> mylabel=awesome
kubectl run -i --tty busybox --image=busybox --restart=Never -- sh
=========================
```

```bash
kubectl create -f 01.pod.yml
```

## Service
```
===== Useful Commands =====
kubectl get service|svc
kubectl delete service <service>
=========================
```