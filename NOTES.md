Any HPA target can be scaled based on the resource usage of the pods in the scaling target. When defining the pod specification the resource requests like cpu and memory should be specified. This is used to determine the resource utilization and used by the HPA controller to scale the target up or down. To use resource utilization based scaling specify a metric source like this:

type: Resource
resource:
  name: cpu
  target:
    type: Utilization
    averageUtilization: 60



## Useful links:

* https://www.powerupcloud.com/autoscaling-based-on-cpu-memory-in-kubernetes-part-ii/

* https://stackoverflow.com/questions/56666532/hpa-not-able-to-fetch-metrics-from-prometheus-in-kubernetes



* https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/#:~:text=The%20Horizontal%20Pod%20Autoscaler%20automatically,other%20application%2Dprovided%20metrics).

* To check kube aggregator https://sysdig.com/blog/kubernetes-autoscaler/#:~:text=Kubernetes%20custom%20metrics%20API,-The%20Kubernetes%20HPA&text=To%20register%20custom%20metrics%20and,the%20Kubernetes%20service%20implementing%20it


edit for metrics server    args:
        - --kubelet-insecure-tls
        - --kubelet-preferred-address-types=InternalIP
        
        
https://docs.aws.amazon.com/eks/latest/userguide/prometheus.html






