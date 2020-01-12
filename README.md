# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

## Tasks

###Installing Node and NPM

This project depends on Nodejs and Node Package Manager (NPM). Before continuing, you must download and install Node (NPM is included) from https://nodejs.com/en/download.

### Setup Docker Environment
You'll need to install docker https://docs.docker.com/install/. Open a new terminal within the project directory and run:

1. Build the images: `docker-compose -f docker-compose-build.yaml build --parallel`
2. Push the images: `docker-compose -f docker-compose-build.yaml push`
3. Run the containers: `docker-compose up`

### Install Kubernetes on AWS Cluster using KubeOne and Terraform

1. Install [Terraform](https://learn.hashicorp.com/terraform/getting-started/install.html)
2. Install [KubeOne](https://github.com/kubermatic/kubeone/blob/master/docs/quickstart-aws.md) and follow the instructions to create the needed infrastructure to deploy the project.
3. Create k8s resources:

```
kubectl apply -f env-config.yml
kubectl apply -f env-secret.yml
kubectl apply -f aws-secret.yml

kubectl apply -f feed-deployment.yml
kubectl apply -f backend-feed-service.yaml

kubectl apply -f user-deployment.yml
kubectl apply -f backend-user-service.yaml

kubectl apply -f reverseproxy-deployment.yml
kubectl apply -f reverseproxy-service.yaml

kubectl apply -f frontend-deployment.yml
kubectl apply -f frontend-service.yaml
```