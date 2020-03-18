# Minikube Grafana Prometheus Monitoring
## Start Minikube Cluster
`minikube start`

## Install helm

`kubectl create serviceaccount tiller --namespace kube-system`

`kubectl create clusterrolebinding tiller-role-binding --clusterrole cluster-admin --serviceaccount=kube-system:tiller`

`helm init --service-account tiller`


`minikube addons enable registry-creds`


## Install premetheus-operator
`helm install stable/prometheus-operator --name=monitoring --namespace=monitoring`

## Show all monitoring pods
`get pods -n monitoring`

## Expose Prometheus
`kubectl port-forward -n monitoring prometheus-monitoring-prometheus-oper-prometheus-0 9090`

## Expose Grafana
> change pods name with grafana pods

`kubectl port-forward -n monitoring monitoring-grafana-ccf87fcd-sqjpm 3000`

- username : admin
- password : prom-operator