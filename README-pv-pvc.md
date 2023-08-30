# 1. PV & PVC Use Case with Example

Below command will deploy Persistent Volume of 5 GB  

    cd examples
    kubectl apply -f pv.yaml

# 2. Create PVC of 1 GB  

    cd examples
    kubectl apply -f pvc.yaml


# 3. Create a Pod using pvc 

    cd examples
    kubectl apply -f pv-pod.yaml