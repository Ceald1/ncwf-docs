# Docs for the Docs


## Harvester Cluster
* Main VM cluster for everything!! And will be the backbone of the whole operation. 
* ONLY admins will have the password for accessing Harvester.
```mermaid
---
config:
  theme: dark
  layout: dagre
---
flowchart TB
    n1["banana (10.3.1.2)"] --> n4["kubevip ip 10.3.1.100"]
    n2["pve (10.3.1.3)"] --> n4
    n3["nebula (10.3.1.4)"] --> n4
    n5[" "]

    n1@{ img: "https://avatars.githubusercontent.com/u/79673333?s=200&v=4", h: 200, w: 200, pos: "b"}
    n4@{ icon: "gcp:cloud-load-balancing", pos: "b", h: 203}
    n2@{ img: "https://avatars.githubusercontent.com/u/79673333?s=200&v=4", h: 200, w: 200, pos: "b"}
    n3@{ img: "https://avatars.githubusercontent.com/u/79673333?s=200&v=4", h: 200, w: 200, pos: "b"}
    n5@{ shape: document, pos: "b", label: "host OS needs between 250 GB to 400GB of storage, rest will be for persistent storage for VMs."}
    n6@{ shape: document, pos: "b", label: "Raw block devices would be preferred."}


```

## Production Cluster
* Kubernetes cluster for all containers.
* Keys stored, backedup, and managed on Next Cloud inside of a VM.
* Things like CTFs will be hosted in this cluster or containers for events and other critical infrastructure that can be containers.

### Cluster Nodes
![aa](./exports/prodCluster-Page-1.png)
* KubeVIP will serve as a load balancer to ensure cluster high availability
* Talos will be used for stability and atomicity as well as ease for rolling back updates

### Key management
![aa](./exports/KeyManagement-Page-1.png)
* Keys will be stored on nextcloud as a backup when keys get lost
* Oauth with itatem will be used as a source of truth to allow existing volunteers with itatem accounts to access their keys if lost.
* Nexcloud will be a virtual machine inside of harvester or on a completely seperate server.
