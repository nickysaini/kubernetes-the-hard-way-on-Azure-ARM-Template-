# Kubernetes Cluster the hard way

This template allows you to create kubernetes cluster with defined number master and worker node. This template also allow to create new VNet or add kubernetes cluster in existing VNet as well.
Also this will created two Load balancer one internal and another external with all required ports of kubernets control plane. SSH NAT rule needs to be allowed manually on required VM on external LB.
