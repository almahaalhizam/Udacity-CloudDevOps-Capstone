# Udacity-CloudDevOps-Capstone

In this project I will applied the skills and knowledge that were developed throughout the Udacity Cloud DevOps Nanodegree program. These include:
  - Working in AWS.
  - Using Jenkins to implement Continuous Integration and Continuous Deployment.
  - Building pipelines.
  - Working with CloudFormation to deploy clusters.
  - Building Kubernetes clusters.
  - Building Docker containers in pipelines.
  
I created a CI/CD pipeline for a simple website that deploys to a cluster in AWS EKS using rolling deployment.

## Project Requirements
  - Jenkins
  - Blue Ocean Plugin in Jenkins
  - Pipeline-AWS Plugin in Jenkins
  - Docker
  - AWS Cli
  - Eksctl
  - Kubectl
  
 All below mentioned screesnhots are found under screesnhots folder.
 
## Project Steps
  1- Launch an Ubuntu EC2 instance where you will setup jenkins, and install all the requirements - screenshot-01.
  
  2- Build a simple application, such as a hello.html or index.html - screenshot-02.
  
  3- and create the Dockerfile to containrize the application - screenshot-03.
  
  4 - Run the command `aws configure` to be able to use Cloudformation to build the infrastructure (networking, cluster, and node groups) in CLI. scripts and files will be found under "deployment" folder.
  
  5- From cloudformation folder, run the following command to create the infrastructure `.\create_stack.sh infra-stack .\infra.yml .\infra-params.json` - screenshot-04.
  
  6- From AWS Console, Navigate to Cloudformation and check if the creation of 'infra-stack' stack is completed - screenshot-05.
  
  7- From cloudformation folder, run the following command to create an eks cluster which will use resources from 'infra-stack' stack ` .\aws_create_stack.sh eks-stack .\eks-cluster.yml .\eks-cluster-params.json` - screenshot-06.
  
  8- From AWS Console, Navigate to Cloudformation and check if the creation of 'eks-stack' stack is completed, it nearly takes time to complete - screenshot-07.
  
  9- From the cloudformation folder, run the following command to create the node-group in the previosuly created cluster `.\aws_create_stack.sh nodegroup-stack .\eks-cluster-nodegroup.yml .\eks-cluster-params.json` - screenshot-08.
  
  10- Check in AWS Console if the 'nodegroup-stack' has been completely created - screenshot-09.
  
  11- There will be 2 Jenkinsfiles, one for first deployment, and the other for rolling deployment. The first depolyment Jenkins pipline will include the following stages ( Lint , Build Docker Image, Push Docker Image to Dockerhub, Deploy containers).
  
  12 - Build the first depolyment Jenkins pipline to include the following stages ( Lint , Build Docker Image, Push Docker Image to Dockerhub, Deploy containers) as found in the file "Jenkins-first-depolyment".
  
  13- Modify the index.html to have wrong syntax in order to show that the Linter is working properly - screesnhot-11. The screenshot shows the Lint stage failing in the pipeline. 
  
  14- Adjust the syntax correctly in index.html and showcase that Linter is working and whole pipeline is successful - screesnhot-12.
  
  15- Run the following command to know that the kubernetes build is successful `kubectl get pods` and `kubectl get services` - screenshot-13.
  
  16- From the output of the previous command: `kubectl get services` , paste the 'External IP/8000' in a browser to access the hello application - screesnhot-14.
  
  17 - Run the other Jenkinsfile to do apply the Rolling deployment - screenshot-15.
  
  
  
  


## Step 5: Test your pipeline
  - Perform builds on your pipeline.
  - Verify that your pipeline works as you designed it.
  - Take a screenshot of the Jenkins pipeline showing deployment and a screenshot of your AWS EC2 page showing the newly created (for blue/green) or modified (for rolling) instances. Make sure you name your instances differently between blue and green deployments.
