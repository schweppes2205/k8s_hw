# HW02

1. In Minikube in namespace kube-system, there are many different pods running. Your task is to figure out who creates them, and who makes sure they are running (restores them after deletion). 

The minicube service that monitors for etcd\apiserver\proxy\scheduler is Kubelet. Coredns has k8s replicaset in deployment

2. Implement Canary deployment of an application via Ingress. Traffic to canary deployment should be redirected if you add "canary:always" in the header, otherwise it should go to regular deployment. Set to redirect a percentage of traffic to canary deployment.

```bash
# create a couple of deployments for a new httpd server 
# with simple index.html (prod & canary). File is gotten from in configmap
$ kubectl apply -f deploy-prod.yaml
$ kubectl apply -f deploy-canary.yaml
# cerate two services for prod and canary deployments
$ kubectl apply -f service-prod.yaml
$ kubectl apply -f service-canary.yaml
# create two ingress rules for prod with no canary specific annotations
# and for canary deployment with canary annotation enabling and with 
# header setting that ingress will be based on to route the traffic
$ kubectl apply -f ingress-prod.yaml
$ kubectl apply -f ingress-canary.yaml
```

Prod example

<img src="img\prod.png">

Canary example

<img src="img\canary.png">