# Install Red Hat SSO on OpenShift
First draft at installing RH-SSO as an authentication provider for OpenShift

login to OpenShift using a cluster-admin user

Change directory to:

```
cd scripts
```

Step #1 - install RH-SSO
```
./createrhsso.sh
```

Step #2 - create OpenShift realm in RH-SSO
```
./createrealm.sh
```

Step #3 - create OpenShift client in RH-SSO
```
./createclient.sh
```


Step #4 - create desired users in RH-SSO   
*Manual entry in the UI, not yet automated

Step #5 - create trusted CA for OpenID provider
```
./createca.sh
```


Step #6 - create resources in ArgoCD

*update the following file or create an Overlay: manifests/app/base/rhsso-openid.yaml  
*issuer must reflect your domain
```
cd ..
oc apply -k cluster/overlay/default
```

Step #7 - Sychronize Argo application
*Currently set to manual sync
