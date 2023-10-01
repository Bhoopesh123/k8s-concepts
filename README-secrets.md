echo -n 'user' > f1.txt
echo -n 'test123' > f2.txt

kubectl create secret generic first-secret \
--from-file=f1.txt \
--from-file=f2.txt

kubectl get secret newsecret -o jsonpath='{.data}'

kubectl exec -it pod-secret -- /bin/bash

ServiceAccount token Secrets
A kubernetes.io/service-account-token type of Secret is used to store a token credential that identifies a ServiceAccount. This is a legacy mechanism that provides long-lived ServiceAccount credentials to Pods.