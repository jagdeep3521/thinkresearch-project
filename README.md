Excercise 1

Design and implement the following infrastructure on a cloud provider (GCP or AWS or Azure) using Terraform (no bash or command line scripts). You may test out your code by signing up for a free account that each of the cloud providers provide. The infrastructure should have at a minimum:
● VPC
● Subnets
● A VM to serve as a bastion/jumper server host
● Kubernetes Cluster

Solution

All infrastructure deliverable output files are located in the outputs directory:
VPC
- Public Subnets
- Route tables
- Internet Gateway
AWS EKS API server endpoint (bastion)
Security groups
EKS cluster with control plane and nodes
Auto-scaling group
LoadBalancer

Pre-requisites:
Installations:
1. aws CLI 
2. eksctl CLI
3. kubectl CLI
4. terraform CLI
5. AWS-IAM-Authenticator

Commands:
`terraform init`
`terraform plan`
`terraform apply`
`terraform state list`
`terraform output kubeconfig > ~/.kube/config`
`kubectl cluster-info`
`kubectl get all --all-namespaces -o wide`

Excercise 2


Suppose you were to deploy a nginx server or a hello-world application on the Kubernetes cluster. How would you structure the deployment YAML?
The deliverable for this exercise will be the YAML files for the Kubernetes deployment. It can be: Yamls only or Helm Chart or Kustomize.​ Please commit the files to the git repository that you will be sharing in your submission

Solution

nginx.yaml --> Contains the deployment and service (exposing the deployment to a LoadBalancer)

Commands:
`kubectl apply -f nginx.yaml`
`kubectl get svc/nginx -o wide`
`kubectl get deployment/nginx -o wide`
- `kubectl exec -it nginx-574b87c764-7z4n2 -- bash` (to confirm that index.html exists in /usr/share/nginx/html inside the pod... Exit after confirming)
After waiting for around a minute, confirm using the LoadBalancer endpoint that you are able to access the "Welcome to nginx" homepage


At the end of both excercise use:
`terraform destroy`
to destroy all resources created by terraform