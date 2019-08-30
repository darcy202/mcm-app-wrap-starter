# A Helm starter to create an MCM application wrap

## Configure Helm client


Identify your $HELM_HOME directory (Tip: `$ helm home` if $HELM_HOME not set)

```
cd $HELM_HOME/starters
git clone https://github.com/darcy202/mcm-app-wrap-starter.git
```


## To use

```
$ helm create mcm-liberty-server00 --starter=mcm-app-wrap-starter
$ helm install --name=mcm-liberty-server00 --set deployable.helm.chartURL="https://github.com/IBM/charts/blob/master/repo/stable/ibm-open-liberty-1.10.0.tgz?raw=true" ./mcm-liberty-server00/ --tls
$ kubectl get applications.app.k8s.io
```