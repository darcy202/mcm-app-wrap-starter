# A Helm starter to create an MCM application wrap

## Configure Helm client


Identify your $HELM_HOME directory (Tip: `$ helm home` if $HELM_HOME not set)

```
cd $HELM_HOME/starters
git clone https://github.com/darcy202/mcm-app-wrap-starter.git
```


## Create new MCM wrap

```
$ helm create mcm-liberty-server00 --starter=mcm-app-wrap-starter
```


## Customise as required

Use values-workload.yaml to override values.yaml in the target deployable Helm chart.
The contents of values-workload.yaml is included in the deployable.yaml template (base64 encoded).


## Deploy

```
$ helm install --name=mcm-liberty-server00 --set deployable.helm.chartURL="https://github.com/IBM/charts/blob/master/repo/stable/ibm-open-liberty-1.10.0.tgz?raw=true" ./mcm-liberty-server00/ --tls
$ kubectl get applications.app.k8s.io
```
Or manage via MCM portal at https://<master>:8443/multicloud/applications