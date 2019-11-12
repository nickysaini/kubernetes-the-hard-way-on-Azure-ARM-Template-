# Provisioning Pod Network

We chose to use CNI - [weave](https://www.weave.works/docs/net/latest/kubernetes/kube-addon/) as our networking option.

### Install CNI plugins

Download the CNI Plugins required for weave on each of the worker nodes - `worker0` and `worker1`

`wget https://github.com/containernetworking/plugins/releases/download/v0.7.5/cni-plugins-amd64-v0.7.5.tgz`

Extract it to /opt/cni/bin directory

`sudo tar -xzvf cni-plugins-amd64-v0.7.5.tgz  --directory /opt/cni/bin/`

### Deploy Weave Network

Deploy weave network. Run only once on the `master0` node.


`kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"`

Weave uses POD CIDR of `10.32.0.0/12` by default.

## Verification

List the registered Kubernetes nodes from the master node:

```
master0$  kubectl get pods -n kube-system -o wide
```

> output

```
NAME              READY   STATUS    RESTARTS   AGE   IP         NODE      NOMINATED NODE   READINESS GATES
weave-net-bjxj8   2/2     Running   0          41s   10.0.0.4   worker0   <none>           <none>
weave-net-jplsn   2/2     Running   0          41s   10.0.0.5   worker1   <none>           <none>
```

Next: [Kube API Server to Kubelet Connectivity](13-kube-apiserver-to-kubelet.md)
