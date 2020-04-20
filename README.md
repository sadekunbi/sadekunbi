# Ansible

## Step By Step Details
- Step 01 - Creating EC2 Instances for Ansible - Manually and with Terraform
- Step 02 - Setting Ansible Project with cfg and ansible hosts
- Step 03 - Playing with Ansible Commands
- Step 04 - Playing with Ansible Host File and Custom Groups
- Step 05 - Creating an Ansible Playbook for Ping
- Step 06 - Understanding Ansible Terminology - Control Node, Managed Nodes, Inventory
- Step 07 - Creating New Ansible Playbook for Executing Shell Commands
- Step 08 - Playing with Ansible Variables
- Step 09 - Creating New Ansible Playbook for Understanding Ansible Facts
- Step 10 - Creating New Ansible Playbook for Installing Apache and Serving HTML
- Step 11 - Reuse and Executing Multiple Ansible Playbooks
- Step 12 - Understanding Conditionals and Loops with Ansible
- Step 13 - Configuring EC2 Dynamic Inventory with Ansible
- Step 14 - Creating AWS EC2 Instances with Ansible
- Step 15 - Providing Declarative Configuration with Ansible
- Step 16 - Deleting all AWS EC2 Instances

### Prerequisites
- 3 EC2 Instances 
    - 2 using Terraform
    - 1 Manually
    - You can use which ever approach you are comfortable with

- EC2 Keys - `ls ~/aws/aws_keys/default-ec2.pem`

- AWS CLI - `aws configure`
```sh
# or
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
```

- boto3 and botocore - For EC2 Dynamic Inventory and Creating EC2 Instances
```sh
# TEst
python
# boto3 quick start
> import boto3
> client = boto3.client('ec2')
```

### Create EC2 Instances using Terraform

```
cd terraform/backup/09-multiple-ec2-instances
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
terraform init
terraform apply
ls ~/aws/aws_keys/ # Make sure that the keys file is present
```

### Ansible Commands

```
cd /in28Minutes/git/devops-master-class/ansible 
ansible --version
ansible -m ping all
ansible all -a "whoami"
ansible all -a "uname"
ssh -vvv -i ~/aws/aws_keys/default-ec2.pem ec2-user@3.83.104.44
ls ~/aws/aws_keys/default-ec2.pem
chmod 400 /Users/rangaraokaranam/aws/aws_keys/default-ec2.pem
ansible all -a "uname"
ansible all -a "uname -a"
ansible all -a "pwd"
ansible all -a "python --version"
ansible dev -a "python --version"
ansible qa -a "python --version"
ansible first -a "python --version"
ansible groupofgroups -a "python --version"
ansible devsubset -a "python --version"
ansible --list-host all
ansible --list-host dev
ansible --list-host first
ansible --list-host \!first
ansible --list-host qa:dev
ansible-playbook playbooks/01-ping.yml
ansible-playbook playbooks/02-shell.yml 
ansible-playbook playbooks/03-variables.yml 
ansible-playbook playbooks/03-variables.yml -e variable1=CommandLineValue
ansible-playbook playbooks/04-ansible-facts.yml 
ansible-playbook playbooks/05-install-apache.yml 
ansible-playbook playbooks/06-playbooks.yml 
ansible-playbook playbooks/06-playbooks.yml --list-tasks
ansible-playbook playbooks/06-playbooks.yml --list-hosts
ansible-playbook playbooks/06-playbooks.yml --list-tags
ansible-playbook -l dev playbooks/01-ping.yml
ansible-playbook playbooks/07-conditionals-and-loops.yml 
ansible-inventory --list
ansible-inventory --graph
ansible-playbook playbooks/08-dynamic-inventory-ping.yml 
ansible-playbook playbooks/09-create-ec2.yml 

```# Azure DevOps

## Azure Marketplace

- Terraform 1 (https://marketplace.visualstudio.com/items?itemName=ms-devlabs.custom-terraform-tasks)
- Terraform 2 (https://marketplace.visualstudio.com/items?itemName=charleszipp.azure-pipelines-tasks-terraform)
- Aws (https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.aws-vsts-tools)

## Projects
- Build and Push Docker Image
- CI/CD/IAAC AWS Kubernetes Cluster
- CI/CD/IAAC Azure Kubernetes Cluster

### Azure DevOps - Pipelines
- Step 01 - Getting Started with Azure DevOps - First Project
- Step 02 - Setting up Git Repo for Azure DevOps Pipeline
- Step 03 - Creating your first Azure DevOps Pipeline
- Step 04 - Getting Started with Azure DevOps - Agents and Jobs - 1
- Step 05 - Getting Started with Azure DevOps - Agents and Jobs - 2
- Step 06 - Using dependsOn with Jobs
- Step 07 - Creating Azure DevOps Pipeline for Playing with Stages 
- Step 08 - Playing with Variables and dependsOn for Stages
- Step 09 - Understanding Azure DevOps Pipeline Variables
- Step 10 - Creating Azure DevOps Tasks for Copy Files and Publish Artifacts
- Step 11 - Running Azure DevOps Jobs on Multiple Agents
- Step 12 - Understanding Azure DevOps Deployment Jobs - Environments and Approvals
- Step 13 - Build and Push Docker Image in Azure DevOps - Part 1
- Step 14 - Build and Push Docker Image in Azure DevOps - Part 2
- Step 15 - Playing with Azure DevOps Releases

### CI, CD, IAAC with Kubernetes on Azure with Azure DevOps - Pipelines
- Step 01 - Review Terraform Configuration for Azure Kubernetes Cluster Creation
- Step 02 - Setting up Client ID, Secret and Public Key for Azure Kubernetes Cluster Creation
- Step 03 - Creating Azure DevOps Pipeline for Azure Kubernetes Cluster IAAC 
- Step 04 - Performing Terraform apply to create Azure Kubernetes Cluster in Azure DevOps
- Step 05 - Connecting to Azure Kubernetes Cluster using Azure CLI
- Step 06 - Creating Azure DevOps Pipeline for Deploying Microservice to Azure Kubernetes
- Step 07 - Creating V2 and Enable Build and Push of Docker Image - Part 1
- Step 08 - Creating V2 and Enable Build and Push of Docker Image - Part 2
- Step 09 - Performing Terraform destroy to delete Azure Kubernetes Cluster in Azure DevOps
- Step 10 - Quick Review of Terraform destroy

### CI, CD, IAAC with Kubernetes on AWS with Azure DevOps - Pipelines
- Step 01 - Review Terraform Configuration for AWS EKS Cluster Creation
- Step 02 - Setup AWS S3 Buckets and Subnet Configuration
- Step 03 - Enable AWS Tools in Azure DevOps and Create Azure DevOps Pipeline
- Step 04 - Performing Terraform apply to create AWS EKS Cluster in Azure DevOps
- Step 05 - Retry Terraform apply for Creating Cluster Binding
- Step 06 - Configure AWS CLI and Setup Kubernetes Connection using Service Account
- Step 07 - Creating Azure DevOps Pipeline for Deploying Microservice to AWS EKS
- Step 08 - Creating V3 and Enable Build and Push of Docker Image - Part 1
- Step 09 - Creating V3 and Enable Build and Push of Docker Image - Part 2
- Step 10 - Performing Terraform destroy to delete AWS EKS Cluster in Azure DevOps - 1
- Step 11 - Performing Terraform destroy to delete AWS EKS Cluster in Azure DevOps - 2

### Azure DevOps - Management Tools
- Step 01 - Getting Started with Azure DevOps with Demo Generator
- Step 02 - Overview of Azure DevOps - Boards, Wiki, Repos and Pipelines
- Step 03 - Exploring Azure DevOps Boards - Epics, Features and User Stories
- Step 04 - Azure DevOps - Boards View vs Backlogs View
- Step 05 - Understanding Sprints in Azure DevOps
- Step 06 - Creating Azure DevOps Queries
- Step 07 - Playing with Azure DevOps Repos
- Step 08 - Quick Review of Azure DevOps Pipelines
- Step 09 - Quick Review of Azure DevOps


## Azure Kubernetes Cluster

Pre-requisites
- Service Account
- SSH Public Key


```
# Create Service Account To Create Azure K8S Cluster using Terraform
az login
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/<<azure_subscription_id>>"

# Create Public Key for SSH Access
ssh-keygen -m PEM -t rsa -b 4096 # PEM - Privacy Enhanced Mail - Certificate Format RSA- Encryption Algorithm

# ls /Users/rangakaranam/.ssh/id_rsa.pub

# Get Cluster Credentials
az aks get-credentials --name <<MyManagedCluster>> --resource-group <<MyResourceGroup>>
```


## AWS EKS Kubernetes Cluster

```
aws configure
aws eks --region us-east-1 update-kubeconfig --name in28minutes-cluster 
kubectl get pods
kubectl get svc
kubectl get serviceaccounts
kubectl get serviceaccounts default -o yaml
kubectl get secret default-token-hqkvj -o yaml
kubectl cluster-info
```

# Backup - DO NOT USE

### Manually setting up from local machine

#### Create Service Account For Your Subscription To Create Azure K8S Cluster using Terraform

```
az login
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/<<azure_subscription_id>>"
export TF_VAR_client_id=<<service_account_appId>>
export TF_VAR_client_secret=<<service_account_password>>
```

#### Create Public Key for SSH Access

```
ssh-keygen -m PEM -t rsa -b 4096 # PEM - Privacy Enhanced Mail - Certificate Format RSA- Encryption Algorithm
ls /Users/rangakaranam/.ssh/id_rsa.pub
```

#### Create Resource Group, Storage Account and Storage Container

```
az group create -l westeurope -n In28minutesK8sResourceGroup
az storage account create -n In28minutesK8sStorageAccount -g In28minutesK8sResourceGroup -l westeurope --sku Standard_LRS
az storage container create -n devterraformstatestorage --account-name <<storage_account_name>> --account-key <<storage_account_key>>

```

#### Execute Terraform Commands

```
# comment backend
terraform init
terraform apply
# add backend
# terraform init with backend
terraform init -backend-config="storage_account_name=<<storage_account_name>>" -backend-config="container_name=<<storage_container_name>>" -backend-config="access_key=<<storage_account_key>>" -backend-config="key=<<k8s.environment.tfstate>>"

```


#### Set Up kubectl 

```
terraform output kube_config>~/.kube/config
```

#### Launch up 

```
kubectl proxy
open 'http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy/#!/overview?namespace=default'
```# Docker

## Projects
- Hello World - Java, JavaScript and Python
- 2 Microservices - Currency Exchange and Currency Conversion

## Steps
- Step 01 - Docker and DevOps - Installation and Introduction
- Step 02 - Your First Docker Usecase
- Step 03 - Important Docker Concepts - Registry, Repository, Tag, Image and Container
- Step 04 - Playing with Docker Images - Java, JavaScript and Python
- Step 05 - Playing with Docker - Detached Mode and Logs
- Step 06 - Playing with Docker Images and Containers
- Step 07 - Understanding Docker Architecture - Docker Client, Docker Engine
- Step 08 - Understanding Docker Popularity - My 3 Top Reasons
- Step 09 - Learning Docker Images - Commands
- Step 10 - Learning Docker Containers - Commands
- Step 11 - Learning Docker Commands - system and stats
- Step 12 - Building Docker Images for Python Application
- Step 13 - Understanding creation of Docker Images in Depth
- Step 14 - Pushing Python App Docker Image to Docker Hub
- Step 15 - Building and Pushing Docker Image for Node JavaScript App
- Step 16 - Building and Pushing Docker Image for Java Application
- Step 17 - Building Efficient Docker Images - Improving Layer Caching
- Step 18 - Understanding ENTRYPOINT vs CMD
- Step 19 - Docker and Microservices - Quick Start
- Step 20 - Introduction to Microservices - CE and CC
- Step 21 - Running Microservices as Docker Containers
- Step 22 - Using Docker Link to Connect Microservices
- Step 23 - Using Custom Networking to Connect Microservices
- Step 24 - Using Docker Compose to Simplify Microservices Launch
- Step 25 - Understanding Docker Compose further


## Registry and Repositories

- https://hub.docker.com/u/in28min
- https://hub.docker.com/r/in28min/hello-world-java
- https://hub.docker.com/r/in28min/hello-world-python
- https://hub.docker.com/r/in28min/hello-world-nodejs

# Commands

```
docker --version
docker run -p 5000:5000 in28min/hello-world-python:0.0.1.RELEASE
docker run -p 5000:5000 in28min/hello-world-java:0.0.1.RELEASE
docker run -p 5000:5000 in28min/hello-world-nodejs:0.0.1.RELEASE
docker run -d -p 5000:5000 in28min/hello-world-nodejs:0.0.1.RELEASE
docker run -d -p 5001:5000 in28min/hello-world-python:0.0.1.RELEASE
docker logs 04e52ff9270f5810eefe1f77222852dc1461c22440d4ecd6228b5c38f09d838e
docker logs c2ba
docker images
docker container ls
docker container ls -a
docker container stop f708b7ee1a8b
docker run -d -p 5001:8080 in28min/hello-world-rest-api:0.0.1.RELEASE
docker pull mysql
docker search mysql
docker image history in28min/hello-world-java:0.0.1.RELEASE
docker image history 100229ba687e
docker image inspect 100229ba687e
docker image remove mysql
docker image remove in28min/hello-world-java:0.0.1.RELEASE
docker container rm 3e657ae9bd16
docker container ls -a
docker container pause 832
docker container unpause 832
docker container stop 832
docker container inspect ff521fa58db3
docker container prune
docker system
docker system df
docker system info
docker system prune -a
docker top 9009722eac4d
docker stats 9009722eac4d
docker container run -p 5000:5000 -d -m 512m in28min/hello-world-java:0.0.1.RELEASE
docker container run -p 5000:5000 -d -m 512m --cpu-quota=50000  in28min/hello-world-java:0.0.1.RELEASE
docker system events

docker container stats 4faca1ea914e3e4587d1d790948ec6cb8fa34f26e900c12632fd64d4722fd59a
docker stats 42f170966ce613d2a16d7404495af7b3295e01aeb9142e1fa1762bbdc581f502

cd /in28Minutes/git/devops-master-class/projects/hello-world/hello-world-python 
docker build -t in28min/hello-world-python:0.0.2.RELEASE . 
docker run -p 5000:5000 -d in28min/hello-world-python:0.0.2.RELEASE
docker history e66dc383f7a0
docker push in28min/hello-world-python:0.0.2.RELEASE

cd ../hello-world-nodejs/
docker build -t in28min/hello-world-nodejs:0.0.2.RELEASE . 
docker container run -d -p 5000:5000 in28min/hello-world-nodejs:0.0.2.RELEASE
docker push in28min/hello-world-nodejs:0.0.2.RELEASE

cd ../hello-world-java/
docker build -t in28min/hello-world-java:0.0.2.RELEASE . 
docker run -d -p 5000:5000 in28min/hello-world-java:0.0.2.RELEASE
docker push in28min/hello-world-java:0.0.2.RELEASE

docker run -d -p 5001:5000 in28min/hello-world-nodejs:0.0.3.RELEASE ping google.com


docker run -d -p 8000:8000 --name=currency-exchange in28min/currency-exchange:0.0.1-RELEASE
docker run -d -p 8100:8100 --name=currency-conversion in28min/currency-conversion:0.0.1-RELEASE

docker network ls
docker network inspect bridge

docker run -d -p 8100:8100 --env CURRENCY_EXCHANGE_SERVICE_HOST=http://currency-exchange --name=currency-conversion --link currency-exchange in28min/currency-conversion:0.0.1-RELEASE

docker network create currency-network
docker container stop currency-exchange
docker container stop currency-conversion
docker run -d -p 8000:8000 --name=currency-exchange --network=currency-network in28min/currency-exchange:0.0.1-RELEASE
docker run -d -p 8100:8100 --env CURRENCY_EXCHANGE_SERVICE_HOST=http://currency-exchange --name=currency-conversion --network=currency-network in28min/currency-conversion:0.0.1-RELEASE

docker-compose --version
cd ../../microservices/
docker-compose up
docker-compose up -d
docker container ls
docker network ls
docker network inspect microservices_currency-compose-network
docker-compose down
docker container ls -a
docker system prune -a
docker-compose config
docker-compose images
docker-compose ps
docker-compose top

```


```
docker build -t in28min/hello-world-java:0.0.1.RELEASE .
docker push in28min/hello-world-java:0.0.1.RELEASE

docker build -t in28min/hello-world-python:0.0.1.RELEASE .
docker push in28min/hello-world-python:0.0.1.RELEASE

docker build -t in28min/hello-world-nodejs:0.0.1.RELEASE .
docker push in28min/hello-world-nodejs:0.0.1.RELEASE
```

### Host Networking in Docker for Mac and Windows

- https://docs.docker.com/network/host/

>The host networking driver only works on Linux hosts, and is not supported on Docker Desktop for Mac, Docker Desktop for Windows, or Docker EE for Windows Server.

# Jenkins

## Projects
- Create Pipeline to Build and Push Docker Image for a Microservice

## Steps
- Step 01 - Introduction and Launching Jenkins as Docker Container
- Step 02 - Initializing Jenkins Plugins and Creating Github Repo
- Step 03 - Setting up Docker and Maven in Jenkins and First Pipeline Run
- Step 04 - Understanding Scripted Pipelines in Jenkins
- Step 05 - Understanding Declarative Pipelines in Jenkins - Stages
- Step 06 - Using Docker Images as Jenkins Pipeline Agents
- Step 07 - Review Pipeline Syntax and Understanding Variables
- Step 08 - Configuring Jenkins Pipeline Path with Docker and Maven Tools
- Step 09 - Running Unit Tests and Integration Tests in Jenkins Pipelines - 1
- Step 10 - Running Unit Tests and Integration Tests in Jenkins Pipelines - 2
- Step 11 - Build and Push Docker Image in Jenkins Pipelines - 1
- Step 12 - Build and Push Docker Image in Jenkins Pipelines - 2
# Hello World Rest API

### Running the Application

Run com.in28minutes.rest.webservices.restfulwebservices.RestfulWebServicesApplication as a Java Application.

- http://localhost:8080/hello-world

```txt
Hello World V1 abcde
```

- http://localhost:8080/hello-world-bean

```json
{"message":"Hello World"}
```

- http://localhost:8080/hello-world/path-variable/in28minutes

```json
{"message":"Hello World, in28minutes"}
```# Kubernetes

## Projects
- Hello World REST API
- 2 Microservices - Currency Exchange and Currency Conversion

## Steps
- Step 01 - Getting Started with Docker, Kubernetes and Google Kubernetes Engine
- Step 02 - Creating Google Cloud Account
- Step 03 - Creating Kubernetes Cluster with Google Kubernete Engine (GKE)
- Step 04 - Review Kubernetes Cluster and Learn Few Fun Facts about Kubernetes
- Step 05 - Deploy Your First Spring Boot Application to Kubernetes Cluster
- Step 06 - Quick Look at Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 07 - Understanding Pods in Kubernetes
- Step 08 - Understanding ReplicaSets in Kubernetes
- Step 09 - Understanding Deployment in Kubernetes
- Step 10 - Quick Review of Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 11 - Understanding Services in Kubernetes
- Step 12 - Quick Review of GKE on Google Cloud Console 
- Step 13 - Understanding Kubernetes Architecture - Master Node and Nodes
- Step 14 - Understand Google Cloud Regions and Zones
- Step 15 - Installing GCloud
- Step 16 - Installing Kubectl 
- Step 17 - Understand Kubernetes Rollouts
- Step 18 - Generate Kubernetes YAML Configuration for Deployment and Service
- Step 19 - Understand and Improve Kubernetes YAML Configuration
- Step 20 - Using Kubernetes YAML Configuration to Create Resources
- Step 21 - Understanding Kubernetes YAML Configuration - Labels and Selectors
- Step 22 - Quick Fix to reduce release downtime with minReadySeconds
- Step 23 - Understanding Replica Sets in Depth - Using Kubernetes YAML Config
- Step 24 - Configure Multiple Kubernetes Deployments with One Service
- Step 25 - Playing with Kubernetes Commands - Top Node and Pod
- Step 26 - Delete Hello World Deployments
- Step 27 - Quick Introduction to Microservices - CE and CC
- Step 28 - Deploy Microservices to Kubernetes
- Step 29 - Understand Environment Variables created by Kubernetes for Services
- Step 30 - Microservices and Kubernetes Service Discovery - Part 1
- Step 31 - Microservices and Kubernetes Service Discovery - Part 2 DNS
- Step 32 - Microservices Centralized Configuration with Kubernetes ConfigMaps
- Step 33 - Simplify Microservices with Kubernetes Ingress - Part 1
- Step 34 - Simplify Microservices with Kubernetes Ingress - Part 2
- Step 35 - Delete Kubernetes Clusters


## Commands

```
docker run -p 8080:8080 in28min/hello-world-rest-api:0.0.1.RELEASE

kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl scale deployment hello-world-rest-api --replicas=3
kubectl delete pod hello-world-rest-api-58ff5dd898-62l9d
kubectl autoscale deployment hello-world-rest-api --max=10 --cpu-percent=70
kubectl edit deployment hello-world-rest-api #minReadySeconds: 15
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE

gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get componentstatuses
kubectl get pods --all-namespaces

kubectl get events
kubectl get pods
kubectl get replicaset
kubectl get deployment
kubectl get service

kubectl get pods -o wide

kubectl explain pods
kubectl get pods -o wide

kubectl describe pod hello-world-rest-api-58ff5dd898-9trh2

kubectl get replicasets
kubectl get replicaset

kubectl scale deployment hello-world-rest-api --replicas=3
kubectl get pods
kubectl get replicaset
kubectl get events
kubectl get events --sort.by=.metadata.creationTimestamp

kubectl get rs
kubectl get rs -o wide
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get rs -o wide
kubectl get pods
kubectl describe pod hello-world-rest-api-85995ddd5c-msjsm
kubectl get events --sort-by=.metadata.creationTimestamp

kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-n6c7l
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-8bhdt

kubectl get componentstatuses
kubectl get pods --all-namespaces

gcloud auth login
kubectl version
gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105

kubectl rollout history deployment hello-world-rest-api
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.3.RELEASE --record=true
kubectl rollout undo deployment hello-world-rest-api --to-revision=1

kubectl logs hello-world-rest-api-58ff5dd898-6ctr2
kubectl logs -f hello-world-rest-api-58ff5dd898-6ctr2

kubectl get deployment hello-world-rest-api -o yaml
kubectl get deployment hello-world-rest-api -o yaml > deployment.yaml
kubectl get service hello-world-rest-api -o yaml > service.yaml
kubectl apply -f deployment.yaml
kubectl get all -o wide
kubectl delete all -l app=hello-world-rest-api

kubectl get svc --watch
kubectl diff -f deployment.yaml
kubectl delete deployment hello-world-rest-api
kubectl get all -o wide
kubectl delete replicaset.apps/hello-world-rest-api-797dd4b5dc

kubectl get pods --all-namespaces
kubectl get pods --all-namespaces -l app=hello-world-rest-api
kubectl get services --all-namespaces
kubectl get services --all-namespaces --sort-by=.spec.type
kubectl get services --all-namespaces --sort-by=.metadata.name
kubectl cluster-info
kubectl cluster-info dump
kubectl top node
kubectl top pod
kubectl get services
kubectl get svc
kubectl get ev
kubectl get rs
kubectl get ns
kubectl get nodes
kubectl get no
kubectl get pods
kubectl get po

kubectl delete all -l app=hello-world-rest-api
kubectl get all

kubectl apply -f deployment.yaml 
kubectl apply -f ../currency-conversion/deployment.yaml 
```# Currency Exchange Micro Service - H2

Run com.in28minutes.microservices.currencyconversionservice.CurrencyConversionServiceApplicationH2 as a Java Application.

## Resources

- http://localhost:8000/currency-exchange/from/USD/to/INR

```json
{
  "id": 10001,
  "from": "USD",
  "to": "INR",
  "conversionMultiple": 65.00,
  "environmentInfo": "NA"
}
```

## H2 Console

- http://localhost:8000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL


## Notes

## Tables Created
```
create table exchange_value 
(
	id bigint not null, 
	conversion_multiple decimal(19,2), 
	currency_from varchar(255), 
	currency_to varchar(255), 
	primary key (id)
)
```

## Containerization

### Troubleshooting

- Problem - Caused by: com.spotify.docker.client.shaded.javax.ws.rs.ProcessingException: java.io.IOException: No such file or directory
- Solution - Check if docker is up and running!
- Problem - Error creating the Docker image on MacOS - java.io.IOException: Cannot run program “docker-credential-osxkeychain”: error=2, No such file or directory
- Solution - https://medium.com/@dakshika/error-creating-the-docker-image-on-macos-wso2-enterprise-integrator-tooling-dfb5b537b44e

### Creating Container

- mvn package

### Running Container

#### Basic
```
docker container run --publish 8000:8000 in28min/currency-exchange:0.0.1-SNAPSHOT
```
# Currency Conversion Micro Service
Run com.in28minutes.microservices.currencyconversionservice.CurrencyConversionServiceApplication as a Java Application.

## Resources

- http://localhost:8100/currency-conversion/from/EUR/to/INR/quantity/10

```json
{
id: 10002,
from: "EUR",
to: "INR",
conversionMultiple: 75,
quantity: 10,
totalCalculatedAmount: 750
}
```

## Containerization

### Troubleshooting

- Problem - Caused by: com.spotify.docker.client.shaded.javax.ws.rs.ProcessingException: java.io.IOException: No such file or directory
- Solution - Check if docker is up and running!
- Problem - Error creating the Docker image on MacOS - java.io.IOException: Cannot run program “docker-credential-osxkeychain”: error=2, No such file or directory
- Solution - https://medium.com/@dakshika/error-creating-the-docker-image-on-macos-wso2-enterprise-integrator-tooling-dfb5b537b44e

### Creating Containers

- mvn package

### Running Containers

```
docker run --publish 8100:8100 --network currency-network --env CURRENCY_EXCHANGE_URI=http://currency-exchange:8000 in28min/currency-conversion:0.0.1-SNAPSHOT
```

#### Test API 
- http://localhost:8100/currency-conversion/from/EUR/to/INR/quantity/10

```
docker login
docker push @@@REPO_NAME@@@/currency-conversion:0.0.1-SNAPSHOT
```

#### Environment Variable

```
        env:     #CHANGE
          - name: CURRENCY_EXCHANGE_URI
            valueFrom:
              configMapKeyRef:
                key: CURRENCY_EXCHANGE_URI
                name: currency-exchange-uri-demo
```### Microservices

These simple microservices enable us to **focus on** learning the tools - Docker, Kubernetes, CI, CD and  build the infrastructure needed around typical microservices.

### Currency Exchange Service

If you ask it the value of 1 USD in INR, or 1 Australian Dollar in INR, the Currency Exchange Service answers 
- 1 USD is 60 INR
- 1 Australian Dollars is 50 INR. 

http://localhost:8000/currency-exchange/from/EUR/to/INR

```json
{
  "id": 10002,
  "from": "EUR",
  "to": "INR",
  "conversionMultiple": 75.00,
  "exchangeEnvironmentInfo": "37f1ad927c6e v1 27c6e"
}
```

### Currency Conversion

Currency Conversion Service is used to convert a bucket of currencies. If you want to find the value of 10 USD, Currency Conversion Service returns 600. 
- **STEP 1** : Currency Conversion Service calls the Currency Exchange Service for the value of 1 USD. It gets a response back saying 60.
- **STEP 2** : The Currency Conversion Service then multiplies 10 by 60, and returns 600 back. 

http://localhost:8100/currency-conversion/from/EUR/to/INR/quantity/10

```json
{
  "id": 10002,
  "from": "EUR",
  "to": "INR",
  "conversionMultiple": 75.00,
  "quantity": 10,
  "totalCalculatedAmount": 750.00,
  "exchangeEnvironmentInfo": "37f1ad927c6e v1 27c6e",
  "conversionEnvironmentInfo": "fb6316b5713d v1 5713d"
}
```

#### How does Currency Conversion know the location of Currency Exchange?
- You don't want to HARDCODE
- Configure an Environment Variable - `CURRENCY_EXCHANGE_SERVICE_HOST`
- --env CURRENCY_EXCHANGE_SERVICE_HOST=http://currency-exchange
# Master Devops - Docker, Kubernetes, Terraform and Azure Devops

## Learn Devops with Docker, Kubernetes, Terraform, Ansible, Jenkins and Azure Devops

## Pipeline Project Github Repositories
- Azure Devops - https://github.com/in28minutes/azure-devops-kubernetes-terraform-pipeline
- Jenkins - https://github.com/in28minutes/jenkin-devops-microservice

## Course Introduction

200+ Videos. 20+ Hours. 6 DevOps Tools - Docker, Kubernetes, Azure Devops, Jenkins, Terraform, and Ansible. 3 Different Clouds - AWS, Azure and Google Cloud. 

Do you need more reasons for enrolling for this amazing course on DevOps?

Do you have ZERO experience with DevOps with Docker, Kubernetes, Azure Devops, Jenkins, Terraform, Ansible, AWS, Azure and Google Cloud? No Problem.

Do you have ZERO experience with DevOps Containers and Container Orchestration with Docker and Kubernetes? No Problem.

Do you have ZERO experience with Continuous Integration or Continuous Delivery in DevOps with Azure Devops and Jenkins? No Problem.

Do you have ZERO experience with the Cloud? No Problem.

Are you ready to learn DevOps with Docker, Kubernetes, Terraform, Ansible, Jenkins and Azure Devops in multiple clouds - AWS, Azure and Google Cloud?

Do you want to join 300,000+ learners having Amazing Learning Experiences with in28Minutes?

Buckle up and Get ready for this wonderful ride on DevOps, Microservices and the Cloud.

Look No Further!

## Course Overview

DevOps is all about People, Process and Tools. In this course, you will understand the basics of DevOps and learn to do DevOps with Docker, Kubernetes, Ansible, Terraform, Azure DevOps and Jenkins. You will learn to implement DevOps with Continuous Integration, Continuous Delivery and Infrastructure as Code. You will play with 3 different clouds - AWS, Azure and Google Cloud.

You will do DevOps with Docker to create and run Docker images for:
- Hello World Applications - Python, JavaScript and Java
- Microservices - Currency Exchange and Currency Conversion

You will learn the basics of Kubernetes on the Google Kubernetes Engine implementing Service Discovery, Centralized Configuration and Load Balancing for Microservices. You will do DevOps with Kubernetes using Terraform (Infrastructure as Code) and Azure DevOps (Continuous Delivery) on multiple cloud platforms (AWS and Azure)

You will learn the basics of Continuous Integration and Continuous Delivery and implement them using Jenkins and Azure DevOps. You will learn to Create Kubernetes Clusters and Deploy Microservices to Kubernetes using Azure DevOps Pipelines on the Cloud with AWS EKS and Azure AKS.

You will learn the basics of Terraform and Ansible and implement Infrastructure as Code. You will provision a number of AWS Resources - EC2 Instances and Load Balancers - using Terraform and configure them with Ansible. You will learn to provision Kubernetes Clusters in AWS and Azure using Terraform. You would learn to run Terraform Configuration in Azure DevOps Pipelines.

This course would be a perfect first step as an introduction to DevOps.


## What you'll learn
- You will learn DevOps with Docker, Kubernetes and Azure DevOps from ZERO, no previous experience required
- You will learn the fundamentals of 6 Most Popular DevOps Tools - Docker, Kubernetes, Azure Devops, Jenkins, Terraform, and Ansible
- You will learn the building blocks of DevOps - Continuous Integration, Continuous Delivery and Infrastructure as Code
- You will learn to implement Azure Devops Pipelines integrating Docker, Kubernetes and  Terraform on AWS EKS and Azure AKS
- You will learn DevOps with Continuous Integration & Continuous Delivery on Azure DevOps and Jenkins
- You will do containerization and container orchestration for microservices with Docker and Kubernetes
- You will play with Docker, Docker Compose and Kubernetes
- You will implement Service Discovery, Centralized Configuration and Load Balancing for Docker Microservices deployed in Kubernetes
- You will Join 300,000 Learners having AMAZING LEARNING Experiences with in28Minutes

## Requirements
- You have an attitude to learn while having fun :)
- You have some programming experience with either Java, Python or JavaScript
- You DO NOT need to have any experience with DevOps, Kubernetes, Docker or Azure DevOps
- We will help you install the tools and create your cloud accounts

## Who is this course for
- You are a programmer wanting to explore DevOps with Docker, Kubernetes and Azure DevOps
- You want to automate deployment of your microservices to the cloud using DevOps with Docker, Kubernetes and Azure DevOps

## Step By Step Details

### Promo
- 00 - Step 00 - Master Devops - Docker, Kubernetes, Terraform and Azure Devops - Promo

### Quick Overview of DevOps
- Step 01 - Master Devops - Docker, Kubernetes, Terraform and Azure Devops - 01 - Intro
- Step 02 - DevOps and Evolution of Software Development 
- Step 03 - Evolution to Agile
- Step 04 - DevOps - An Overview

### Start DevOps with Docker
- Step 00 00 - DevOps and Containerization
- Step 01 - Docker and DevOps - Installation and Introduction
- Step 02 - Your First Docker Usecase
- Step 03 - Important Docker Concepts - Registry, Repository, Tag, Image and Container
- Step 04 - Playing with Docker Images - Java, JavaScript and Python
- Step 05 - Playing with Docker - Detached Mode and Logs
- Step 06 - Playing with Docker Images and Containers
- Step 07 - Understanding Docker Architecture - Docker Client, Docker Engine
- Step 08 - Understanding Docker Popularity - My 3 Top Reasons
- Step 09 - Learning Docker Images - Commands
- Step 10 - Learning Docker Containers - Commands
- Step 11 - Learning Docker Commands - system and stats
- Step 12 - 01 - Import Docker Projects into Visual Studio Code
- Step 12 - 02 - Building Docker Images for Python Application
- Step 13 - Understanding creation of Docker Images in Depth
- Step 14 - Pushing Python App Docker Image to Docker Hub
- Step 15 - Building and Pushing Docker Image for Node JavaScript App
- Step 16 - Building and Pushing Docker Image for Java Application
- Step 17 - Building Efficient Docker Images - Improving Layer Caching
- Step 18 - Understanding ENTRYPOINT vs CMD
- Step 19 - Docker and Microservices - Quick Start
- Step 20 - Introduction to Microservices - CE and CC
- Step 21 - Running Microservices as Docker Containers
- Step 22 - Using Docker Link to Connect Microservices
- Step 23 - Using Custom Networking to Connect Microservices
- Step 24 - Using Docker Compose to Simplify Microservices Launch
- Step 25 - Understanding Docker Compose further

### DevOps with Kubernetes on Google Kubernetes Engine
- Step 01 - Getting Started with Docker, Kubernetes and Google Kubernetes Engine
- Step 02 - Creating Google Cloud Account
- Step 03 - Creating Kubernetes Cluster with Google Kubernete Engine (GKE)
- Step 04 - Review Kubernetes Cluster and Learn Few Fun Facts about Kubernetes
- Step 05 - Deploy Your First Spring Boot Application to Kubernetes Cluster
- Step 06 - Quick Look at Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 07 - Understanding Pods in Kubernetes
- Step 08 - Understanding ReplicaSets in Kubernetes
- Step 09 - Understanding Deployment in Kubernetes
- Step 10 - Quick Review of Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 11 - Understanding Services in Kubernetes
- Step 12 - Quick Review of GKE on Google Cloud Console 
- Step 13 - Understanding Kubernetes Architecture - Master Node and Nodes
- Step 14 - Understand Google Cloud Regions and Zones
- Step 15 - Installing GCloud
- Step 16 - Installing Kubectl
- Step 17 - Understand Kubernetes Rollouts
- Step 18 - Generate Kubernetes YAML Configuration for Deployment and Service
- Step 19 - Understand and Improve Kubernetes YAML Configuration
- Step 20 - Using Kubernetes YAML Configuration to Create Resources
- Step 21 - Understanding Kubernetes YAML Configuration - Labels and Selectors
- Step 22 - Quick Fix to reduce release downtime with minReadySeconds
- Step 23 - Understanding Replica Sets in Depth - Using Kubernetes YAML Config
- Step 24 - Configure Multiple Kubernetes Deployments with One Service
- Step 25 - Playing with Kubernetes Commands - Top Node and Pod
- Step 26 - Delete Hello World Deployments
- Step 27 - Quick Introduction to Microservices - CE and CC
- Step 28 - Deploy Microservices to Kubernetes
- Step 29 - Understand Environment Variables created by Kubernetes for Services
- Step 30 - Microservices and Kubernetes Service Discovery - Part 1
- Step 31 - Microservices and Kubernetes Service Discovery - Part 2 DNS
- Step 32 - Microservices Centralized Configuration with Kubernetes ConfigMaps
- Step 33 - Simplify Microservices with Kubernetes Ingress - Part 1
- Step 34 - Simplify Microservices with Kubernetes Ingress - Part 2
- Step 35 - Delete Kubernetes Clusters

### Getting Started with Terraform
- Step 00 00 - Getting Started with Infrastructure as Code
- Step 00 01 - Getting Started with Terraform
- Step 01 - Creating and Initializing First Terraform Project
- Step 02 - Create AWS IAM User Access Key and Secret
- Step 03 - Configure Terraform Environment Variables for AWS Access Keys
- Step 04 - Creating AWS S3 Buckets with Terraform
- Step 05 - Playing with Terraform State - Desired, Known and Actual
- Step 06 - Playing with Terraform Console
- Step 07 - Creating AWS IAM User with Terraform
- Step 08 - Updating AWS IAM User Name with Terraform
- Step 09 - Understanding Terraform tfstate files in depth
- Step 10 - gitignore Terraform tfstate files
- Step 11 - Refactoring Terraform files - Variables, Main and Outputs
- Step 12 - Creating Terraform Project for Multiple IAM Users
- Step 13 - Playing with Terraform Commands - fmt, show and console
- Step 14 - Recovering from Errors with Terraform
- Step 15 - Understanding Variables in Terraform
- Step 16 - Creating Terraform Project for Understanding List and Map
- Step 17 - Adding Elements - Problem with Terraform Lists
- Step 18 - Creating Terraform Project for Learning Terraform Maps
- Step 19 - Quick Review of Terraform FAQ
- Step 20 - Understanding Creation of EC2 Instances in AWS Console
- Step 21 - Creating New Terraform Project for AWS EC2 Instances
- Step 22 - Creating New EC2 Key Pair and Setting Up
- Step 23 - Adding AWS EC2 Configuration to Terraform Configuration
- Step 24 - Installing Http Server on EC2 with Terraform - Part 1
- Step 25 - 01 - Installing Http Server on EC2 with Terraform - Part 2
- Step 25 - 02 - Immutable Servers with Infrastructure as Code
- Step 26 - Remove hardcoding of Default VPC with AWS Default VPC
- Step 27 - Remove hardcoding of subnets with Data Providers
- Step 28 - Remove hardcoding of AMI with Data Providers
- Step 29 - Playing with Terraform Graph and Destroy EC2 Instances
- Step 30 - Creating New Terraform Project for AWS EC2 with Load Balancers
- Step 31 - Create Security Group and Classic Load Balancer in Terraform
- Step 32 - Review and Destroy AWS EC2 with Load Balancers
- Step 33 - Creating Terraform Project for Storing Remote State in S3
- Step 34 - Create Remote Backend Project for Creating S3 Buckets
- Step 35 - Update User Project to use AWS S3 Remote Backend
- Step 36 - Creating multiple environments using Terraform Workspaces
- Step 37 - Creating multiple environments using Terraform Modules

### Learn Azure DevOps - Continuous Integration, Deployment and Delivery
- Step 00 00 - Getting Started with Continuous Integration, Deployment and Delivery
- Step 00 01 - Getting Started with Azure DevOps
- Step 01 - Getting Started with Azure DevOps - First Project
- Step 02 - Setting up Git Repo for Azure DevOps Pipeline
- Step 03 - Creating your first Azure DevOps Pipeline
- Step 04 - Getting Started with Azure DevOps - Agents and Jobs - 1
- Step 05 - Getting Started with Azure DevOps - Agents and Jobs - 2
- Step 06 - Using dependsOn with Jobs
- Step 07 - Creating Azure DevOps Pipeline for Playing with Stages
- Step 08 - Playing with Variables and dependsOn for Stages
- Step 09 - Understanding Azure DevOps Pipeline Variables
- Step 10 - Creating Azure DevOps Tasks for Copy Files and Publish Artifacts
- Step 11 - Running Azure DevOps Jobs on Multiple Agents
- Step 12 - Understanding Azure DevOps Deployment Jobs - Environments and Approvals
- Step 13 - Build and Push Docker Image in Azure DevOps - Part 1
- Step 14 - Build and Push Docker Image in Azure DevOps - Part 2
- Step 15 - Playing with Azure DevOps Releases

### CI, CD and IAAC on Azure AKS Kubernetes Clusters with Docker, Azure DevOps and Terraform
- Step 00 - Getting Started with IAAC for Azure AKS with Azure DevOps, Terraform and Kubernetes
- Step 01 - Review Terraform Configuration for Azure Kubernetes Cluster Creation
- Step 02 - Setting up Client ID, Secret and Public Key for Azure Kubernetes Cluster Creation
- Step 03 - Creating Azure DevOps Pipeline for Azure Kubernetes Cluster IAAC
- Step 04 - Performing Terraform apply to create Azure Kubernetes Cluster in Azure DevOps
- Step 05 - 01 - Installing Azure CLI
- Step 05 - 02 - Connecting to Azure Kubernetes Cluster using Azure CLI
- Step 06 - 01 - Creating Azure DevOps Pipeline for Deploying Microservice to Azure Kubernetes
- Step 06 - 02 - Managing Pipelines and Github Repositories for Kubernetes and Microservices
- Step 07 - Creating V2 and Enable Build and Push of Docker Image - Part 1
- Step 08 - Creating V2 and Enable Build and Push of Docker Image - Part 2
- Step 09 - Performing Terraform destroy to delete Azure Kubernetes Cluster in Azure DevOps
- Step 10 - Quick Review of Terraform destroy

### CI, CD and IAAC on AWS EKS Kubernetes Clusters with Docker, Azure DevOps and Terraform
- Step 00 - Geting Started with IAAC for AWS EKS with Azure DevOps, Terraform and Kubernetes
- Step 01 - Review Terraform Configuration for AWS EKS Cluster Creation
- Step 02 - Setup AWS S3 Buckets and Subnet Configuration
- Step 03 - Enable AWS Tools in Azure DevOps and Create Azure DevOps Pipeline
- Step 04 - Performing Terraform apply to create AWS EKS Cluster in Azure DevOps
- Step 05 - Retry Terraform apply for Creating Cluster Binding
- Step 06 - 01 - Installing AWS CLI
- Step 06 - 02 - Configure AWS CLI and Setup Kubernetes Connection using Service Account
- Step 07 - Creating Azure DevOps Pipeline for Deploying Microservice to AWS EKS
- Step 08 - Creating V3 and Enable Build and Push of Docker Image - Part 1
- Step 09 - Creating V3 and Enable Build and Push of Docker Image - Part 2
- Step 10 - Performing Terraform destroy to delete AWS EKS Cluster in Azure DevOps - 1
- Step 11 - Performing Terraform destroy to delete AWS EKS Cluster in Azure DevOps - 2

### Learn Azure DevOps with Boards and Backlogs
- Step 01 - Getting Started with Azure DevOps with Demo Generator
- Step 02 - Overview of Azure DevOps - Boards, Wiki, Repos and Pipelines
- Step 03 - Exploring Azure DevOps Boards - Epics, Features and User Stories
- Step 04 - Azure DevOps - Boards View vs Backlogs View
- Step 05 - Understanding Sprints in Azure DevOps
- Step 06 - Creating Azure DevOps Queries
- Step 07 - Playing with Azure DevOps Repos
- Step 08 - Quick Review of Azure DevOps Pipelines
- Step 09 - Quick Review of Azure DevOps

### Learn Continuous Integration with Jenkins
- Step 00 01 - Getting Started with Jenkins
- Step 01 - Introduction and Launching Jenkins as Docker Container
- Step 02 - Initializing Jenkins Plugins and Creating Github Repo
- Step 03 - Setting up Docker and Maven in Jenkins and First Pipeline Run
- Step 04 - Understanding Scripted Pipelines in Jenkins
- Step 05 - Understanding Declarative Pipelines in Jenkins - Stages
- Step 06 - Using Docker Images as Jenkins Pipeline Agents
- Step 07 - Review Pipeline Syntax and Understanding Variables
- Step 08 - Configuring Jenkins Pipeline Path with Docker and Maven Tools
- Step 09 - Running Unit Tests and Integration Tests in Jenkins Pipelines - 1
- Step 10 - Running Unit Tests and Integration Tests in Jenkins Pipelines - 2
- Step 11 - Build and Push Docker Image in Jenkins Pipelines - 1
- Step 12 - Build and Push Docker Image in Jenkins Pipelines - 2

### Getting Started with Ansible
- Step 00 01 - Getting Started with Ansible
- Step 01 - Creating EC2 Instances for Ansible - Manually and with Terraform
- Step 02 - Setting Ansible Project with cfg and ansible hosts
- Step 03 - Playing with Ansible Commands
- Step 04 - Playing with Ansible Host File and Custom Groups
- Step 05 - Creating an Ansible Playbook for Ping
- Step 06 - Understanding Ansible Terminology - Control Node, Managed Nodes, Inventory
- Step 07 - Creating New Ansible Playbook for Executing Shell Commands
- Step 08 - Playing with Ansible Variables
- Step 09 - Creating New Ansible Playbook for Understanding Ansible Facts
- Step 10 - Creating New Ansible Playbook for Installing Apache and Serving HTML
- Step 11 - Reuse and Executing Multiple Ansible Playbooks
- Step 12 - Understanding Conditionals and Loops with Ansible
- Step 13 - 01 - Getting Ready for EC2 Dynamic Inventory with Ansible
- Step 13 - 02 - Configuring EC2 Dynamic Inventory with Ansible
- Step 14 - Creating AWS EC2 Instances with Ansible
- Step 15 - Providing Declarative Configuration with Ansible
- Step 16 - Deleting all AWS EC2 Instances

### Appendix - Installing Visual Studio Code 
- Step 01 - Installing VS Code
- Step 02 - Download and Setup Projects in Visual Studio Code

### Appendix - Introduction to Microservices
- Step 01 - Introduction to Microservices
- Step 02 - Advantages of Microservices

### Appendix - Exploring Microservice Projects
- Step 01 - Code Review - Microservices

### Appendix - Getting Started with AWS
- Step 01 - Creating an AWS Root Account
- Step 02 - Creating an IAM User for your AWS Account
- Step 03 - Its Your Responsibility to Monitor Billing on the Cloud - 5 Recommendations
- Step 04 - Monitor AWS Billing - Setting Billing Alerts

### Appendix - Getting Started with Azure
- Step 01 - Creating an Azure Account
- Step 02 - Exploring Cloud Best Practices - Minimize Costs

### Appendix - DevOps Best Practices and Perspectives
- Step 01 - DevOps - Break down the wall
- Step 02 - DevOps Perspectives - CAMS
- Step 03 - DevOps Best Practices
- Step 04 - DevOps Perspectives - Continuous DevOps
- Step 05 - DevOps Maturity Assessment - Questions to ask

#### Required Tools
- Visual Studio Code
- Docker
- Docker Compose
- AWS Account
- AWS CLI
- Azure Account
- Azure CLI
- Google Cloud Account
- Terraform 
- Ansible

## Next Steps

## Diagrams

```

graph architecture {

node[style=filled,color="#59C8DE"]
//node [style=filled,color="#D14D28", fontcolor=white];
rankdir = LR
node[shape=record, width=1.6]


ParentNode1 -- ChildNode1
ChildNode1 -- ChildNode2
ChildNode1 -- ChildNode3
ChildNode1 -- ChildNode4

ParentNode1[label=<Configuration <BR/>and Scripts>]
ChildNode1[label=<Ansible>];
ChildNode2[label=<Server 1>];
ChildNode3[label=<Server 2>];
ChildNode4[label=<Server 3>];

}

graph architecture {
layout="circo";
node[style=filled,  fillcolor="#D14D28", fontcolor=white]
//node [style=filled,color="#D14D28", fontcolor=white];
rankdir = LR
node[shape = circle,  width=1]
edge [dir=forward]

Node1 -- Node2
Node2 -- Node3
Node3 -- Node4
Node4 -- Node1
//Node4 -- Node5
//Node5 -- Node6

Node1[label=<DEV>]
Node2[label=<QA>]
Node3[label=<STAGE>]
Node4[label=<PROD>]
//Node5[label=<5>]
//Node6[label=<6>]

}


graph architecture {
rankdir = LR
node[shape = circle,  width=1, style=filled,fillcolor="#59C8DE"]
//shape = record
edge [dir=forward]

Node1 -- Node2
Node2 -- Node3
Node3 -- Node4
//Node4 -- Node1
//Node4 -- Node5
//Node5 -- Node6

Node1[label=<DEV>]
Node2[label=<QA>]
Node3[label=<STAGE>]
Node4[label=<PROD>]
//Node5[label=<5>]
//Node6[label=<6>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1, style=filled,fillcolor="#59C8DE"]
//shape = record
edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node5 -- Node6
Node6 -- Node7
Node7 -- Node1
Node1 -- Node2
Node2 -- Node3

Node1[label=<Code>]
Node2[label=<Build>]
Node3[label=<Test>]
Node4[label=<Release>]
Node5[label=<Deploy>]
Node6[label=<Review>]
Node7[label=<Plan>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1.3, style=filled,color="#59C8DE", fontcolor=black]
//shape = record
//fillcolor="#59C8DE"
//edge [dir=forward]
edge [width=0]
#D14D28

Node3 -- Node4[style=invis]
Node4 -- Node5[style=invis]
Node1 -- Node2[style=invis]
Node2 -- Node3[style=invis]

Node1[label=<Business>]
Node2[label=<Architecture>]
Node3[label=<Development>]
Node4[label=<Testing>]
Node5[label=<Operations>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1, style=filled,color="#D14D28", fontcolor=white]
//shape = record
//fillcolor="#59C8DE"
edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node5 -- Node6
Node1 -- Node2
Node2 -- Node3

Node1[label=<Vision>]
Node2[label=<Iteration 1>]
Node3[label=<Iteration 2>]
Node4[label=<...>]
Node5[label=<Iteration n>]
Node6[label=<Product>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1, style=filled,fillcolor="#59C8DE"]
//shape = record
edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node5 -- Node6
Node6 -- Node7
Node7 -- Node8
Node8 -- Node1
Node1 -- Node2
Node2 -- Node3

Node1[label=<Code>]
Node2[label=<Build>]
Node3[label=<Test>]
Node4[label=<Release>]
Node5[label=<Deploy>]
Node6[label=<Operate>]
Node7[label=<Monitor>]
Node8[label=<Plan>, fillcolor=white]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=2, style=filled,fillcolor="#D14D28", fontcolor=white]
//shape = record
//edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node5 -- Node6
Node6 -- Node7
Node7 -- Node8
Node8 -- Node1
Node1 -- Node2
Node2 -- Node3

Node1[label=<<FONT POINT-SIZE="20">Continuous<br/>Planning</FONT>>]
Node2[label=<<FONT POINT-SIZE="20">Continuous<br/>Development</FONT>>]
Node3[label=<<FONT POINT-SIZE="20">Continuous<br/>Integration</FONT>>]
Node4[label=<<FONT POINT-SIZE="20">Continuous<br/>Deployment</FONT>>]
Node5[label=<<FONT POINT-SIZE="20">Continuous<br/>Testing</FONT>>]
Node6[label=<<FONT POINT-SIZE="20">Continuous<br/>Delivery</FONT>>]
Node7[label=<<FONT POINT-SIZE="20">Continuous<br/>Monitoring</FONT>>]
Node8[label=<<FONT POINT-SIZE="20">Continuous<br/>Feedback</FONT>>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1.6, style=filled,fillcolor="#D14D28", fontcolor=white]
//shape = record
edge [dir=forward]
{ rank=same Node1 Node2 Node3 }
{ rank=same Node7 Node8 Node9 }

Node3 -- Node4
Node4 -- Node5
Node5 -- Node6
Node6 -- Node7
Node7 -- Node8
Node8 -- Node9
Node1 -- Node2
Node2 -- Node3

Node1[label=<<FONT POINT-SIZE="20">Code<br/>Commit</FONT>>]
Node2[label=<<FONT POINT-SIZE="20">Unit<br/>Tests</FONT>>]
Node3[label=<<FONT POINT-SIZE="20">Integration<br/>Tests</FONT>>]
Node4[label=<<FONT POINT-SIZE="20">Package<br/></FONT>>]
Node5[label=<<FONT POINT-SIZE="20">Deploy</FONT>>]
Node6[label=<<FONT POINT-SIZE="20">Automated<br/> Tests</FONT>>]
Node7[label=<<FONT POINT-SIZE="20">Testing<br/>Approval</FONT>>, fillcolor=white, fontcolor=black]
Node8[label=<<FONT POINT-SIZE="20">Deploy<br/>NEXT</FONT>>]
Node9[label=<<FONT POINT-SIZE="20">..</FONT>>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1.6, style=filled,fillcolor="#D14D28", fontcolor=white]
//shape = record
edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node1 -- Node2
Node2 -- Node3

Node1[label=<<FONT POINT-SIZE="20">Provision<br/>Server</FONT>>]
Node2[label=<<FONT POINT-SIZE="20">Install<br/>Java</FONT>>]
Node3[label=<<FONT POINT-SIZE="20">Install<br/>Tomcat</FONT>>]
Node4[label=<<FONT POINT-SIZE="20">Configure<br/>Tomcat</FONT>>]
Node5[label=<<FONT POINT-SIZE="20">Deploy<br/>Application</FONT>>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1.6, style=filled,fillcolor="#D14D28", fontcolor=white]
//shape = record
edge [dir=forward]

Node3 -- Node4
Node4 -- Node5
Node1 -- Node2
Node2 -- Node3

Node1[label=<<FONT POINT-SIZE="20">Create<br/>Template</FONT>>]
Node2[label=<<FONT POINT-SIZE="20">Provision<br/>Server</FONT>>]
Node3[label=<<FONT POINT-SIZE="20">Install<br/>Software</FONT>>]
Node4[label=<<FONT POINT-SIZE="20">Configure<br/>Software</FONT>>]
Node5[label=<<FONT POINT-SIZE="20">Deploy<br/>App</FONT>>]

}

graph architecture {
rankdir = LR
node[shape = circle,  width=1.6, style=filled,fillcolor="#D14D28", fontcolor=white]
//shape = record
edge [dir=forward]

Node3 -- Node4
Node1 -- Node2
Node2 -- Node3

Node1[label=<<FONT POINT-SIZE="20">Provision<br/>Server v1</FONT>>]
Node2[label=<<FONT POINT-SIZE="20">Provision<br/>Server v2</FONT>>]
Node3[label=<<FONT POINT-SIZE="20">Remove<br/>Server v1</FONT>>]
Node4[label=<<FONT POINT-SIZE="20">..<br/></FONT>>]

}
```

## Todo
- Course Promotion
  - 2 Emails on Udemy
  - 2 Emails to Email List
  - Create YouTube Course Preview Video
    - Add YouTube Course Preview Video as End Video for all videos
    - Make it the YouTube Default Video
  - Release atleast 20 small videos - one a day on Youtube
  - Do atleast 3 Youtube live sessions
  - After a Month
    - UFB# Terraform

## Projects
- Provision EC2 based HTTP Servers with Load Balancer
- Provision AWS and Azure Kubernetes Clusters (Azure DevOps Pipelines)

## Steps
- Step 01 - Creating and Initializing First Terraform Project
- Step 02 - Create AWS IAM User Access Key and Secret
- Step 03 - Configure Terraform Environment Variables for AWS Access Keys
- Step 04 - Creating AWS S3 Buckets with Terraform
- Step 05 - Playing with Terraform State - Desired, Known and Actual
- Step 06 - Playing with Terraform Console
- Step 07 - Creating AWS IAM User with Terraform
- Step 08 - Updating AWS IAM User Name with Terraform
- Step 09 - Understanding Terraform tfstate files in depth
- Step 10 - gitignore Terraform tfstate files
- Step 11 - Refactoring Terraform files - Variables, Main and Outputs
- Step 12 - Creating Terraform Project for Multiple IAM Users
- Step 13 - Playing with Terraform Commands - fmt, show and console
- Step 14 - Recovering from Errors with Terraform
- Step 15 - Understanding Variables in Terraform
- Step 16 - Creating Terraform Project for Understanding List and Map
- Step 17 - Adding Elements - Problem with Terraform Lists
- Step 18 - Creating Terraform Project for Learning Terraform Maps 
- Step 19 - Quick Review of Terraform FAQ
- Step 20 - Understanding Creation of EC2 Instances in AWS Console
- Step 21 - Creating New Terraform Project for AWS EC2 Instances
- Step 22 - Creating New EC2 Key Pair and Setting Up
- Step 23 - Adding AWS EC2 Configuration to Terraform Configuration
- Step 24 - Installing Http Server on EC2 with Terraform - Part 1
- Step 25 - Installing Http Server on EC2 with Terraform - Part 2
- Step 26 - Remove hardcoding of Default VPC with AWS Default VPC
- Step 27 - Remove hardcoding of subnets with Data Providers
- Step 28 - Remove hardcoding of AMI with Data Providers
- Step 29 - Playing with Terraform Graph and Destroy EC2 Instances
- Step 30 - Creating New Terraform Project for AWS EC2 with Load Balancers
- Step 31 - Create Security Group and Classic Load Balancer in Terraform
- Step 32 - Review and Destroy AWS EC2 with Load Balancers
- Step 33 - Creating Terraform Project for Storing Remote State in S3 
- Step 34 - Create Remote Backend Project for Creating S3 Buckets
- Step 35 - Update User Project to use AWS S3 Remote Backend
- Step 36 - Creating multiple environments using Terraform Workspaces
- Step 37 - Creating multiple environments using Terraform Modules



## Commands Executed

```
brew install terraform
terraform --version
terraform version
terraform init
export AWS_ACCESS_KEY_ID=*******
export AWS_SECRET_ACCESS_KEY=*********
terraform plan
terraform console
terraform apply -refresh=false
terraform plan -out iam.tfplan
terraform apply "iam.tfplan"
terraform apply -target=aws_iam_user.my_iam_user
terraform destroy
terraform validate
terraform fmt
terraform show
export TF_VAR_iam_user_name_prefix = FROM_ENV_VARIABLE_IAM_PREFIX
export TF_VAR_iam_user_name_prefix=FROM_ENV_VARIABLE_IAM_PREFIX
terraform plan -refresh=false -var="iam_user_name_prefix=VALUE_FROM_COMMAND_LINE"
terraform apply -target=aws_default_vpc.default
terraform apply -target=data.aws_subnet_ids.default_subnets
terraform apply -target=data.aws_ami_ids.aws_linux_2_latest_ids
terraform apply -target=data.aws_ami.aws_linux_2_latest
terraform workspace show
terraform workspace new prod-env
terraform workspace select default
terraform workspace list
terraform workspace select prod-env
```