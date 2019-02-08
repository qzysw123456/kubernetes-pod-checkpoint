# kubernetes-pod-checkpoint
## Introduction
Checkpointing is an important technique in the realm of distributed system. For some batch jobs(especially for machine learning jobs or any other big data processing pipeline can run several days), failure is inevitable. Without checkpointing this kind of application can never finish. Another well know utilization is live migration. Live migration enables moving application from one physical machine to another with minimal downtime for clients.

Kubernetes, Google’s open source project for cluster orchestration, does not presently support pod level checkpointing. In this project, I would more than welling to make an experimental effort to implement checkpointing mechanism for Kubernetes.


## Mission Time Line
### Quest: How is restart policy implemented in Kubernetes Feb.6. 2019
Kubernetes has restart policy, for application with "always" attribute, kube-controller would restart another instance after one instance is down. But if I want to implement the checkpointing feature, this restart policy doesn't make any sense. Since I dont want my application be restart from its orgin status automatically. So it is very important to figure out which part of code implement the restart policy
#### Subquest: Container pause Feb. 7. 2019
Inside a pod, a pause container is always started with the container I desired. It looks like some kind of daemon that controls the other container. But after investigation, this container is used for maintaining namespace for all containers inside one pod.
