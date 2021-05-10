## Prometheus setup + HPA 

#### Steps to setup Prometheus
Note: Everything is in namespace monitoring until mentioned otherwise<br>

* helm repo add bitnami https://charts.bitnami.com/bitnami<br>
* helm install prometheus bitnami/kube-prometheus -f values.yaml -n monitoring<br>
* To access Prometheus from outside the cluster execute the following commands<br>
<i>nohup  kubectl port-forward --namespace monitoring svc/kube-prometheus-prometheus 9090:9090 &</i><br>

* Make sure application and service monitors are deployed with clusterBinding - specific to application
* Prometheus should be up and running and scrape metrics from all namespaces (for reference use https://github.com/hr1sh1kesh/multi-tenant-monitoring/tree/master/prometheus-per-ns)

### Steps to setup metrics server

* kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
* kubectl get deployment metrics-server -n kube-system

**Important:** Ensure the tls certs are in place to enable handshake
Ref: https://docs.aws.amazon.com/eks/latest/userguide/metrics-server.html
<br>

### Steps to setup HPA
* kubectl autoscale deployment ~deply-name~ --cpu-percent=50 --min=1 --max=10

<br>Ref: https://docs.aws.amazon.com/eks/latest/userguide/horizontal-pod-autoscaler.html
  
**Important:** Resource request and limits need to be set for all containers - HPA will not work without it
