ConfigMaps are “unchanged” if the data hasn’t changed.  
Secrets are always “configured” — even if the file hasn’t changed

# 1. Create Opaque secrets using file

Arbitrary user-defined data Secret and it is the default secret in Kubernetes.

    echo -n 'user' > f1.txt
    echo -n 'test123' > f2.txt

    kubectl create secret generic first-secret \
    --from-file=f1.txt \
    --from-file=f2.txt

# 2. Create Opaque secrets using manifest and use it in a pod

    cd examples
    kubectl apply -f secret.yaml
    kubectl apply -f pod-secret.yaml
    kubectl exec -it pod-secret -- /bin/bash

# 3. Create Service Account Token Secret

A kubernetes.io/service-account-token type of Secret is used to store a token credential that identifies a ServiceAccount. This is a legacy mechanism that provides long-lived ServiceAccount credentials to Pods.

    cd examples
    kubectl apply -f secret2.yaml

# 4. Docker config Secrets:

Stores the credentials for accessing a Docker registry for images.

    docker login
    cat ~/.docker/config.json

    kubectl create secret generic regcred \
    --from-file=.dockerconfigjson=/home/bhoopesh/.docker/config.json \
    --type=kubernetes.io/dockerconfigjson

    cd examples
    kubectl apply -f secret6.yaml
    kubectl apply -f pod-secret3.yaml

# 5. Basic authentication Secret:

Used for storing credentials needed for basic authentication. When using this Secret type, the `data` field of the Secret must contain the `username` and `password` keys

    cd examples
    kubectl apply -f secret3.yaml


# 6. SSH authentication secrets:

Used for storing data used in SSH authentication. When using this Secret type, you will have to specify a `ssh-privatekey` key-value pair in the `data` (or `stringData`) field as the SSH credential to use.

    cd examples
    kubectl apply -f secret4.yaml

# 7. TLS secrets:

For storing a certificate and its associated key that are typically used for TLS . This data is primarily used with TLS termination of the Ingress resource, but may be used with other resources or directly by a workload. When using this type of Secret, the `tls.key` and the `tls.crt` key must be provided in the data (or `stringData`) field of the Secret configuration

    cd examples
    kubectl apply -f secret5.yaml