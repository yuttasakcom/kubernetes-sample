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
$ kubectl cluster-info

```

## Sample

```bash
# create deployment
$ kubectl run echoserver --image=k8s.gcr.io/echoserver:1.6 --port=8080

# expose deployment / create service
$ kubectl expose deployment echoserver --type=NodePort

# show url
$ minikube service echoserver --url

# delete deployment
$ kubectl delete deployment echoserver

# minikube stop
$ minikube stop
```

## Pod

```bash
# create pod
$ kubectl create -f 01.pod.yaml # basic
$ kubectl apply -f 01.pod.yaml # advance

# delete pod
$ kubectl delete -f 01.pod.yml

===== Useful Commands =====
kubectl get pod
kubectl describe pod <pod name>
kubectl logs -f <pod name>
kubectl expose pod <pod name> --port=8080 --name=name-service
kubectl port-forward <pod name> 8080:8080
kubectl attach <pod name> -i
kubectl exec <pod name> -- command
kubectl label pods <pod name> mylabel=awesome
kubectl run -i --tty busybox --image=busybox --restart=Never -- sh

kubectl get pods -o wide
=========================
```

## Service

```
===== Useful Commands =====
$ kubectl apply -f 02.service.yaml
$ minikube port
# http://192.168.99.100:31000

$kubectl get service|svc
$kubectl delete service <service>
=========================
```

## Deployment

```
===== Useful Commands =====
kubectl get deployments
kubectl get rs
kubectl get pods --show-labels
kubectl rollout status deployment/echoserver
kubectl set image deployment/echoserver echoserver=gcr.io/google-containers/echoserver:1.6
kubectl edit deployment/echoserver
kubectl rollout history deployment/echoserver
kubectl rollout undo deployment/echoserver
kubectl rollout undo deployment/echoserver --to-revision=n
kubectl scale deployments/<deployment name> --replicas=4
=========================
```

## Command

```bash
$ eval $(minikube docker-env)
```
