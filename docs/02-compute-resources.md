# Provisioning Compute Resources

Note: You must have Azure Subscription with enough permission to create Azure resources.

Download this github repository and Deploy the templates provided in Auzre folder.

`git clone https://github.com/nickysaini/kubernetes-the-hard-way-on-Azure-ARMTemplate.git`

Using Azure Portal.
`https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy-portal`

Using Azure Powershell & cloud Shell
`https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy`


This does the below:

- Deploys Virtual Network with one subnet - 1,3,5 Master in AV Set with Managed disk, Worker nodes in AV Set with managed disk, 1 internal & External Loadbalancer and with publilc IP attched with external LB also all required ports are open on internal LB to allow communication with kubernetes control plane
    > This is the default settings. This can be changed in provided ARM templates. 

- Default Set's IP addresses in the range 10.0.0.0/16 CIDR and subnet range 10.0.0.0/24. All VMs master & worker will be assigned static internal IP.

- Add's a DNS entry to each of the nodes to access internet
    > DNS: 8.8.8.8
To update DNS in all VM script added in Tools folder. 

- Install's Docker on all Worker nodes
To install docker on worker node script added in tool folder.


## SSH to the nodes

Use your favourite SSH Terminal tool (putty).


## Verify Environment

- Ensure all VMs are up
- Ensure LBs are created.
- Ensure you can SSH into these VMs using the IP and private keys or password
- Ensure the VMs can ping each other
- Ensure the worker nodes have Docker installed on them.
  > command `sudo docker version`