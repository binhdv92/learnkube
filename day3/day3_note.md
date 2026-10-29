	1. Review day2
	2. Networking
	3. Traffic flow on cluster.
	4. How service work.
	5. How 

Review:
Api server:
- central point of contact for all components
- read/writes data from etcd
- we know also that it provides authentication, authorization.

Controller manager:
- takes action based on notifications from etcd via the api-server.
- made up of a bunch of components that manage all the k8s resources
- in response to these updates, persists changes to etcd.

Scheduler
- assigning pods to nodes (one at a time)
- two major steps: filtering, scoring.
- also handles storage (particularly: pvc).

etcd:
- holds the config for the cluster.
- key-value store
- distributed for high availability
- RAFT, leader, follower, candidate.
- clusters with odd number of nodes (9 max).

kubelet:
- kubernetes 'agent', runs on worker nodes (all actually)
- compares the state of the node to the control plane.
- apply changes to kep it in sync (particularly, running pods)
- probes run here too.

Scheduling:
- filtering (what doesn't meet the criteria?)
- scoring (which is the best node out of the candidates?)
- pods have selectors

Taints and Tolerations:
- kubectl taint nodes node1 key1=value1:NoSchedule
UNLESS

NoSchedule: don't schedule the pod on it.
PreferNoSchedule: ... unless you have no other choice
NoExecute: ... AND EVICT existing pods that don't have the toleration.

CORDONING:
- kubectl cordon NODE

TEMPLATING:
- `sed` <-- nothing wrong with this.
- `yq` <-- isn't kubernetes aware.
- `Kustomize` <-- both yaml and k8s aware
- `HELM` <-- text-oriented, not yaml
    - values.yaml: the only place to change.
- `KRO`: 