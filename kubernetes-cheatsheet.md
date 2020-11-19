# Kubernetes
---

##### 1 .What is a kubernetes cluster?

* Collection of computers, which work as a single unit. 
* Consists of two things :-
* Master  -`Coordinates the cluster` 
* Node - `Workers which run the application.`

Each 'node' has a kubelet which is an agent to manage the node and communicate with kubernetes master.

Nodes communicates with master using the `Kubernetes API`. This API can be used by us to communicate directly with the cluster.

----
#### Minikube

Deploys a one node cluster in a VM locally. Usually used for testing purposes.

- Start a cluster
`minikube start`
----
#### Kubectl 
A CLI for executing commands on the cluster.

- Check the cluster details.
 `kubectl cluster-info`
- To view the nodes in a cluster.
`kubectl get nodes`

##### Deployment :-

- Deploy an application :- 
 `kubectl create deployment <deployment-name> --image=<image-location>`

- Get Deployments
`kubectl get deployments`

- Create a proxy 
`kubectl proxy`

This will create a connection between the host and the cluster. The proxy enables direct access to the API's from the terminal.

##### Troubleshooting with kubectl :-

- Get a list of pods
`kubectl get pods`

- Check what containers are running inside the pods.
`kubectl describe pods`
Also shows more information including IP's, ports used etc.

- View the container logs
`kubectl logs <pod-name>` (can specifiy container name too)

- Executing commands on container
`kubectl exec <container-name> <command>`
----
#### Using Service to expose apps.
- Creating a service and exposing it to external traffic
`kubectl expose <deployment-name> --type=NodePort --port 8080`
----
#### Scaling an application.

- Scale up
`kubectl scale <deployment-name> --replicas=<number>`
- Scale down
`kubectl scale <deployment-name> --replicas=<number>`
----
#### Updating applications

- Changing the image
`kubectl set image <deployment-name>=<new-image-version>`
- Confirm the update using rollout
`kubectl rollout status <deployment-name>`
-Rollback an update
`kubectl rollout undo <deployment-name>`
----
#### Dashboard
- Enable the dashboard using minikube:-
`minikube addons enable dashboard` (Have to use a yaml file for deployment and config, check [here.](https://www.katacoda.com/courses/kubernetes/launch-single-node-cluster)
