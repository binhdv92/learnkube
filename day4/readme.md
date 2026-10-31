# Networking
if an IP address:
- was on the same network as you -> talk to it directly.
- isn't on the same network as you -> forward to the gateway.

# K8S networking rules:
- a pod should be able to talk to any other pod (without the use of NAT)
- processes and services on a given node should be able to talk to pods on that node.

-> we need a flat network.

192.168.1.0/24 for the nodes
10.0.X.0/24 for the pods, where X is the last octet of the node.

~ 65ooo pods.

Limitaition:
- multi-data center can have clashing subnets.
- encrypt trafict?
- we don't have control of the network at all.

Software-based overlay networks are a common solution!

Flannel, Cilium

Consequence:
-No gateway?
- Adding CPU, latency
- Encryption!
- we don't have to be on the same network node-to-node.

# Internal Networking.
Single pod talking to many pods.
That's done through the Service.
- No guarantees to have an IP (Headless)
- If there is an IP, that IP isn't "REAL" like 172.0.0.0
- it just dat in etcd that translates to cluster behaviour.

Headless:
- No IP, load balancing is done by client.
- using DNS (CoreDNS)
- if on the same namespace, call it just `red` instead of `red.<namespace>

ClusterIP
- Assign a IP (non-routable)
- kube-proxy creates intercept and rewrite rules using iptables

# External Networking
NodePort
- expose a port on every node
- put a load balance in front.

# Load Balancer.
- Does the VM provisioning for you

OSI layer 3/4. IP, port.

# Ingress
- ingress manifest yaml
- ingress controller, deployment that run an http reverse proxy that understand services, endpoint objects.


# Gateway API
- Separation of concerns
- Similar to ingress, headers, verbs, traffic splitting.

# Service Mesh
- control plan
- data plane (sidecar proxies).
-  typically envoy proxy as MITM.
- encrytion between pods
- policies (path, domain, verb).
-traffic shaping, 1% to one deployment, 99% to another.
- distributed tracing.


# API
kubectl apply -f resource.yaml
-> I am talking to the API.
- Client side validation
- service discovery (what resources, versions)

Authentification
- Normal user account (human beings)
- service account (processes, eg: ingress controller, kube-proxy)
    - using yaml

UserInfo:
- username
- uid
- groups
- additional info

-> authorization (what I can do?)
- node (kubelets)
- RBAC
    Role, ClusterRole
    RoleBinding, ClusterRoleBinding

Admission Controllers
- mutating
- schema validation
- validation admission controllers.
- validating admission controllers.
    policy servers (kyverno, etc)
    Raw policy using CEL

Resource Handles
- prep to store in etcd, then write

API Aggregator
- reverse proxy for the api
- register 3rd