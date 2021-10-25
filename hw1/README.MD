# HW01

1. 
Run `kubectl run web --image=nginx:latest`. Take a look at created resource in cmd "kubectl get pods"  
<img src="img\kubectlGetPods01.png">

2. 
Take a look at created resource in Dashboard
<img src="img\PodsInDashboard01.png">

3. 
Take a look at created resource in cmd
<img src="img\dockerPs01.png">

4. 
Execute:
``` bash
$ kubectl apply -f pod.yaml
$ kubectl apply -f rs.yaml
$ kubectl get pod
```
<img src="img\kubectlGetPods02.png">
<img src="img\RSInDashboard02.png">

5. 
Create a deployment nginx. Set up two replicas. Remove one of the pods, see what happens.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-hw
spec:
  replicas: 2
  selector:
    matchLabels:
      application: nginx-hw
  template:
    metadata:
      labels:
        application: nginx-hw
    spec:
      containers:
        - name: nginx-hw
          image: nginx:latest
          ports:
            - containerPort: 80
```
`kubectl get pod`:  
<img src="img\kubectlGetPods03.png">

Pods in dashboard:

<img src="img\PodsInDashboard03.png">

Removing one pod. Checking result with `kubectl` and dashboard:

<img src="img\kubectlGetPodsAfterDelete03.png">
<img src="img\PodsInDashboardAfterDelete02.png">

