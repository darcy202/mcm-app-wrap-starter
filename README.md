Tested on MCM 3.2.0

# Helm starters to bootstrap an MCM application

This repo includes example MCM applications to quickly bootstrap a new MCM application deployment.
The example MCM application wraps are provided as Helm starters, allowing you to bootstrap a new Helm chart application from these.
As for the target deployable, examples include both Helm chart(s) and native K8s.



## Configure Helm client with these MCM app starters


Identify your $HELM_HOME directory (Tip: `$ helm home` if $HELM_HOME not set).
Copy contents of this repo into `$HELM_HOME/starters`.

```
git clone https://github.com/darcy202/mcm-app-wrap-starter.git
cp -r mcm-app-wrap-starter/* $HELM_HOME/starters
```

## Example 1: Target deployable = Helm chart(s)

### Bootstrap a new MCM application using the mcm-app-helm starter

```
$ helm create mcm-liberty-server00 --starter=mcm-app-helm
```

### Customise as required

Where the target deployable is a Helm chart, you can use values-workload.yaml to override values.yaml in the target deployable Helm chart. The contents of values-workload.yaml is included in the deployable.yaml template (base64 encoded).

### Deploy

```
$ helm install --name=mcm-liberty-server00 --set deployable.helm.chartURL="https://github.com/IBM/charts/blob/master/repo/stable/ibm-open-liberty-1.10.0.tgz?raw=true" ./mcm-liberty-server00/ --tls
$ kubectl get applications.app.k8s.io
```
Or manage via MCM portal at https://\<master>:8443/multicloud/applications




## Example 2: Target deployable = native Kubernetes yaml

### Bootstrap a new MCM application using the mcm-app-k8s starter

```
$ helm create mcm-nginx-server00 --starter=mcm-app-k8s
```

### Customise as required

Where the target deployable is native Kubernetes yaml, you can just reference your values.yaml directly since the target yaml is embedded in `templates/deployable.yaml`.

### Deploy

```
$ helm install --name=mcm-nginx-server00 ./mcm-nginx-server00/ --tls
$ kubectl get applications.app.k8s.io
```
Or manage via MCM portal at https://\<master>:8443/multicloud/applications