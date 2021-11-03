# Kubernetes cource homework
## [Homework01](https://github.com/schweppes2205/k8s_hw/tree/main/hw1)
## [Homework02](https://github.com/schweppes2205/k8s_hw/tree/main/hw2)

Notes for me from the future:

- installation on remote virtual machine (centos 8.0). no virtualization. only docker => minikube start --vm-driver=none;

- default docker installation with routine from docker portal;

- resolving warning from minicube start like by installing packs of enabling\disabling feature:
    - [WARNING Swap]: running with swap on is not supported. Please disable swap;
    - [WARNING FileExisting-socat]: socat not found in system path;
    - [WARNING FileExisting-tc]: tc not found in system path;
    - [WARNING Service-Kubelet]: kubelet service is not enabled, please run 'systemctl enable kubelet.service'.

- firewalld is disabled, selinux is disabled;

- docker runtime used cgroupfs, kubelet started with systemd. resolution:
`minikube start --vm-driver=none --extra-config=kubelet.cgroup-driver=cgroupfs`

- for some reason Update deployment after metric server installation did not went well. [Resolution](http://www.mtitek.com/tutorials/kubernetes/install-kubernetes-metrics-server.php).

- remote installation did not provided a http access with proxy. Service method changed from clusterIp to [NodePort](https://github.com/kubernetes/dashboard/blob/master/docs/user/accessing-dashboard/README.md#nodeport);

- [A new user needs to be created](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md) to access. default did not worked well for some reason:

- secret retrieve oneliner: `kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"`