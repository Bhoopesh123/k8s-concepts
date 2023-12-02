Environment Variable Creation for Containers 

# Description 
When you create a Pod, you can set environment variables for the containers that run in the Pod. To set environment variables, include the env or envFrom field in the configuration file. 

The env and envFrom fields have different effects. 

env
    allows you to set environment variables for a container, specifying a value directly for each variable that you name. 
envFrom
    allows you to set environment variables for a container by referencing either a ConfigMap or a Secret. When you use envFrom, all the key-value pairs in the referenced ConfigMap or Secret are set as environment variables for the container. You can also specify a common prefix string. 

# 1. Create a Pod with Environment Variable

    cd examples
    kubectl apply -f env1.yaml
    kubectl exec envar-demo -- printenv

    kubectl apply -f env2.yaml

# 2. Create a Pod with Environment Variable from Configmap and from Secret.


    cd examples
    kubectl apply -f envconfigmap.yaml
    kubectl apply -f envsecret.yaml
    kubectl apply -f env3.yaml
    kubectl exec envar-demo3 -- printenv



