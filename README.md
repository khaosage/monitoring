# monitoring
k8s monitoring


## Deploy Charts
create a monitoring namespace
`kubectl create ns monitoring`

Deploy helm charts
`helm -n monitoring prometheus-operator prometheus-operator/`
`helm -n monitoring grafana grafana/`

## Deploy extra manifests to monitor externals

Raspberry PI.
```
kubectl apply -f pi_endpoint/service.yaml
kubectl apply -f pi_endpoint/endpoints.yaml
kubectl apply -f pi_endpoint/servicemonitor.yaml
```

## port-forward localhost
```
kubectl port-forward -n monitoring svc/view-grafana 3000:3000
kubectl port-forward -n monitoring svc/pagwe-prometheus-operator-prometheus 9090:9090
kubectl port-forward -n monitoring svc/alertmanager-operated 9093:9093
```
