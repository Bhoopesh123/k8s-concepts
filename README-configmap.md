# 1. Configmap Documentation  

Use Secrets for things that are actually secret like API keys, credentials, etc
Use ConfigMaps for not-secret configuration data


ConfigMaps are “unchanged” if the data hasn’t changed.
Secrets are always “configured” — even if the file hasn’t changed