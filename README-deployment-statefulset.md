# 1. Deployment Use Case with Example

Below command will deploy nginx deployment  

    cd examples
    kubectl apply -f deployement_explanation.yaml

# Updating a Deployment  

    kubectl set image deployment.v1.apps/nginx-deployment nginx=nginx:1.16.1
    kubectl rollout status deployment/nginx-deployment
    kubectl get rs
    kubectl describe deployments

# Rolling Back a Deployment  

    kubectl set image deployment/nginx-deployment nginx=nginx:1.161
    kubectl get rs

# Checking Rollout History of a Deployment  

    kubectl rollout history deployment/nginx-deployment
    kubectl rollout history deployment/nginx-deployment --revision=2
    kubectl rollout undo deployment/nginx-deployment

# Scaling a Deployment  

    kubectl scale deployment/nginx-deployment --replicas=10
    kubectl autoscale deployment/nginx-deployment --min=10 --max=15 --cpu-percent=80

# 2. StatefulSet Use Case with Example

Below command will deploy statefulset deployment  

    cd examples
    kubectl apply -f statefulset_explanation.yaml