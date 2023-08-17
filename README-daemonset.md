# 1. Daemonset Use Case with Example

Below command will deploy fluent-d daemonset  

    cd examples
    kubectl create ns logging
    kubectl apply -f daemonset.yaml

# 2. Apply Taint and Tolerations For Daemonset  

There are 3 effects:

1. NoSchedule: Kubernetes scheduler will only allow scheduling pods that have tolerations for the tainted nodes.

2. PreferNoSchedule: Kubernetes scheduler will try to avoid scheduling pods that don’t have tolerations for the tainted nodes.

3. NoExecute: Kubernetes will evict the running pods from the nodes if the pods don’t have tolerations for the tainted nodes.

Tainted a node:
    kubectl taint node k3d-mykeptn-server-0 app=fluentd-logging:NoExecute
    kubectl apply -f daemonset.yaml

Untainted of a Node:
    kubectl taint node k3d-mykeptn-server-0 app=fluentd-logging:NoExecute-

    kubectl label node k3d-mykeptn-server-0 type=platform-tools
    kubectl apply -f daemonset2.yaml

# 3. Nodeselector For Daemonset Pods  

We can use nodeSelector to run the pods on some specific nodes. 
DaemonSet controller will create Pods on nodes that match the node selector’s key and value

    kubectl label node k3d-mykeptn-server-0 type=platform-tools
    kubectl apply -f daemonset2.yaml