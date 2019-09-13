# A Helm starter to create an MCM application wrap

## Configure Helm client


Identify your $HELM_HOME directory (Tip: `$ helm home` if $HELM_HOME not set)

```
git clone https://github.com/darcy202/mcm-app-wrap-starter.git
cp -r mcm-app-wrap-starter/* $HELM_HOME/starters
```


## Create new MCM wrap

Where your target deployable is a Helm chart use:

```
$ helm create mcm-liberty-server00 --starter=mcm-app-helm
```

Where the target deployable is native Kubernetes yaml, use:

```
$ helm create mcm-nginx-server00 --starter=mcm-app-k8s
```


## Customise as required

Where the target deployable is a Helm chart, you can use values-workload.yaml to override values.yaml in the target deployable Helm chart. The contents of values-workload.yaml is included in the deployable.yaml template (base64 encoded).

Where the target deployable is native Kubernetes yaml, you can just reference your values.yaml directly since the target yaml is embedded in your deployable.yaml.


## Deploy

```
$ helm install --name=mcm-liberty-server00 --set deployable.helm.chartURL="https://github.com/IBM/charts/blob/master/repo/stable/ibm-open-liberty-1.10.0.tgz?raw=true" ./mcm-liberty-server00/ --tls
$ kubectl get applications.app.k8s.io
```
Or manage via MCM portal at https://<master>:8443/multicloud/applications