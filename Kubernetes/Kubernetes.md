>Kubernetes is an open-source container orchestration system for automating software deployment, scaling, and management. Google originally designed Kubernetes, but the Cloud Native Computing Foundation now maintains the project.

## Architecture
- The Kubernetes cluster is made of [[Pods]]
- [[Deployments]] are objects in Kubernetes that lets you manage a set of identical pods.
	- Without a deployment, you’d need to create, update, and delete a bunch of pods manually.
	- With a deployment, you declare a single object in a YAML file. This object is responsible for creating the pods, making sure they stay up to date, and ensuring there are enough of them running.
	- You can also easily autoscale your applications using a Kubernetes deployment.
- [[Services]] are used to allow network access to a set of pods.
	- A service is an abstraction which defines a logical set of Pods and a policy by which to access them (sometimes this pattern is called a micro-service).
	- You can use deployments independent of services. You can use services independent of deployments. They just go together really nicely!

![[KubernetesArchitecture.png]]
