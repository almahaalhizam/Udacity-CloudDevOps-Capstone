# Udacity-CloudDevOps-Capstone

In this project I will applied the skills and knowledge that were developed throughout the Udacity Cloud DevOps Nanodegree program. These include:
  - Working in AWS.
  - Using Jenkins to implement Continuous Integration and Continuous Deployment.
  - Building pipelines.
  - Working with CloudFormation to deploy clusters.
  - Building Kubernetes clusters.
  - Building Docker containers in pipelines.
  
I created a CI/CD pipeline for a simple website that deploys to a cluster in AWS EKS using rolling deployment.

# Project Requirements
  - Jenkins
  - Blue Ocean Plugin in Jenkins
  - Pipeline-AWS Plugin in Jenkins
  - Docker
  - AWS Cli
  - Eksctl
  - Kubectl
  
 All below mentioned screesnhots are found under screesnhots folder.
 
# Project Steps
  1- Launch an Ubuntu EC2 instance where you will setup jenkins, and install all the requirements - screenshot-01.
  2- Build a simple application, such as a hello.html (index.html), and create the Dockerfile to containrize the application - screenshot-02.
  3- Run the command "aws configure" to be able to use Cloudformation to build the infrastructure (networking, cluster, and node groups) in CLI. scripts and files will be found under "deployment" folder.
  4- From cloudformation folder, run the following command to create the infrastructure ".\create_stack.sh infra-stack .\infra.yml .\infra-params.json"
  5- From AWS Console, Navigate to Cloudformation and check if the creation of 'infra-stack' stack is completed.
  6-From cloudformation folder, run the following command to create an eks cluster which will use resources from 'infra-stack' stack " .\aws_create_stack.sh eks-stack .\eks-cluster.yml .\eks-cluster-params.json"
  7- From AWS Console, Navigate to Cloudformation and check if the creation of 'eks-stack' stack is completed, it nearly takes about 12-20 min.
  8- From the cloudformation folder, run the following command to create the node-group in the previosuly created cluster ".\aws_create_stack.sh nodegroup-stack .\eks-cluster-nodegroup.yml .\eks-cluster-params.json"
  9- Check in AWS Console if the 'nodegroup-stack' has been completely created.
  
------------------------------------------------------------------------------------------------------------------------
  
## Step 3: Pick AWS Kubernetes as a Service, or build your own Kubernetes cluster.
  - Use Ansible or CloudFormation to build your “infrastructure”; i.e., the Kubernetes Cluster.
  - It should create the EC2 instances (if you are building your own), set the correct networking settings, and deploy software to these instances.
  - As a final step, the Kubernetes cluster will need to be initialized. The Kubernetes cluster initialization can either be done by hand, or with Cloudformation at the student’s discretion.
  
## Step 4: Build your pipeline
  - Construct your pipeline in your GitHub repository.
  - Set up all the steps that your pipeline will include.
  - Configure a deployment pipeline.
  - Include your Dockerfile/source code in the Git repository.
  - Include with your Linting step both a failed Linting screenshot and a successful Linting screenshot to show the Linter working properly.

## Step 5: Test your pipeline
  - Perform builds on your pipeline.
  - Verify that your pipeline works as you designed it.
  - Take a screenshot of the Jenkins pipeline showing deployment and a screenshot of your AWS EC2 page showing the newly created (for blue/green) or modified (for rolling) instances. Make sure you name your instances differently between blue and green deployments.
