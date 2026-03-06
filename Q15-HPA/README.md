### Question 

Create a new HorizontalPodAutoscaler (HPA ) named apache-server in the autoscale namespace. This HPA must target the existing Deployment called apache-server in the autoscale namespace. 
Set the HPA to aim for 50% CPU usage per Pod . Configure it to have at least 1 Pod and no more than 4 Pods . 
Also, set the downscale stabilization window to 30 seconds
