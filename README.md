# Kubernetes-MS
- [Docker](https://docs.docker.com/get-started/) 
  - installation: https://docs.docker.com/desktop/install/mac-install/
  
- [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters. You can use kubectl to deploy applications, inspect and manage cluster resources, and view logs. 
  - Run the installation command: `brew install kubectl` 
  - Verify kubectl configuration: `kubectl cluster-info`
https://kubernetes.io/docs/setup/

- [minikube](https://minikube.sigs.k8s.io/docs/) : minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes. install:
`brew install minikube`
    - Start your cluster: `minikube start`
    - Interact with your cluster: `minikube kubectl -- get po -A`
    - Manage your cluster
https://minikube.sigs.k8s.io/docs/handbook/

- YAML - YAML is a concise data serialization language, which is typically considered easier to read than the more verbose JSON or XML. It is most often used in configuration files of servers and software applications. 
  - https://yamlchecker.com/

1. Crearte a namespace: `kubectl apply -f namespace.yaml` 
2. Get namespaces: `kubectl get namespaces`
3. Delete namespaces: `kubectl delete -f namespace.yaml`
4. Deploy an application: `kubectl apply -f deployment.yaml`
5. Verfiy deployment: `kubectl get deployments -n development`
6. Get pods: `kubectl get pods -n development`
7. Delete pod: `kubectl delete pod POD_NAME -n development` (verify terminated and new one created)
8. Check that your application is working: `kubectl describe pod POD_NAME -n development`
9. View application logs: `kubectl logs POD_NAME -n development`

## Expose your application to the internet with a LoadBalancer
 A Kubernetes service is a load balancer that directs traffic from the internet to Kubernetes pods. A load balancer service has a public and static IP address. The public IP address means that anyone can access it from the internet, and the static part is important because your pods and their IP addresses change frequently, but your service IP needs to remain the same.
`LoadBalancer/service.yaml` contains a 
- Connect to LoadBalancer services : `sudo minikube tunnel` 
- create namespace: `kubectl apply -f namespace.yaml`
- apply the LoadBalancer service: `kubectl apply -f service.yaml`
- apply the pods : `kubectl apply -f deployment.yaml`

Open 127.0.0.1 and see the exposed pod.

## Add resource requests and limits to your pod
https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/


### Deploying our application to Kubernetes
We're ready to deploy our application to Kubernetes, but let's take a look at our assets.
