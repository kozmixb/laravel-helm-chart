# Cert Manager

For handling certifications within the cluster cert-manager.io is being used.
Reason for using a ClusterIssuer config so this setup can be used across all namespaces

## Getting started

Before applying the config, cert-manager custom resources needs to be imported

cert-manager.io
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.10.1/cert-manager.yaml
```

Once it is done, make sure `EMAIL_ADDRESS` field is pointing to a valid email address
and then

```
kubectl apply -f letsencrypt-prod.yaml
```

## How to use

To use this cert you need to include in your ingress config file 

```
metadata:
  annotations: 
    cert-manager.io/cluster-issuer: "letsencrypt-prod"
```