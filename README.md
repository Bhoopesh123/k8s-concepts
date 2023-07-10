# Control Plane Components :
The control plane's components make global decisions about the cluster
    Detecting and responding to cluster events 
    Scheduling
    starting up a new pod when a deployment's replicas field is unsatisfied

    1. kube-apiserver: (Front End of Control Plane)
      The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane
      kube-apiserver is designed to scale horizontally
      You can run several instances of kube-apiserver and balance traffic between those instances

    2. etcd:
      Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.

    3. kube-scheduler:
      Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.

    4. kube-controller-manager:
      Each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.
      Some types of these controllers are:

        a. Node controller: Responsible for noticing and responding when nodes go down.
        b. Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
        c. EndpointSlice controller: Populates EndpointSlice objects (to provide a link between Services and Pods).
        d. ServiceAccount controller: Create default ServiceAccounts for new namespaces

    5. cloud-controller-manager: (Absent for Minikube since it is Local)
      The cloud controller manager lets you link your cluster into your cloud provider's API.
      The cloud-controller-manager only runs controllers that are specific to your cloud provider

# Node Components:
Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

    1. kubelet: An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.
    The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy

    2. kube-proxy: kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept.
    kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.

# Container runtime:
    The container runtime is the software that is responsible for running containers.
    Kubernetes supports container runtimes such as containerd, CRI-O, and any other implementation of the Kubernetes CRI (Container Runtime Interface).

    Container Run Time in Nutshell:
    https://kubernetes.io/docs/setup/production-environment/container-runtimes/


![image](https://github.com/Bhoopesh123/k8s-concepts/assets/43882719/a6a5a553-78e4-4d67-afaa-4e86fc1d83f3)
