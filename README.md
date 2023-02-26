# Simple Apache Web App using EKS
## Pre-requisite: 
Set up a Jenkins CICD pipeline that built and publish a simple web application to DockerHub(codes for web app was download from startbootstrap.com)

In this project, I am using Kubernetes to orchestrate the deployment of a simple web app on the AWS platform.
The image for the exercise was sources from my publicly repo on DockerHub (mooma/website:2.2)
STEPS
1.  Create an EKS cluster without nodegroup using default settings.
    - eksctl create cluster --name playgound --region us-west-2 --version 1.24  --without-nodegroup
2.  Create a node group made up of three nodes
    eksctl create nodegroup \
      --cluster playground-cluster \
      --region us-west-2 \
      --name playground-ng \
      --node-ami-family AmazonLinux2 \
      --node-type m5.large \
      --nodes 3 \
      --nodes-min 3 \
      --nodes-max 4 \
      --ssh-access \
      --ssh-public-key us-west2-key
3.  Create a deployment manifest for Apache webserver then run
    - kubectl apply -f deployment-name
4.  Create a service manifest with the service type loadbalancer listening on port 80, then run
    - kubectl apply -f service-name
5.  copy loadbalancer external ip and past in a browser