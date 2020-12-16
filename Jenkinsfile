pipeline {
    agent any
   
    stages {

		stage('Lint HTML') {
			 steps {
				sh 'tidy -q -e *.html'
			}
		}
    
    stage('Build Docker image') {
        steps {
          sh 'docker build -t app .'
      }
    }
    stage('Push Docker Image') {
              steps {
                  withDockerRegistry([url: "", credentialsId: "dockerhub-id"]) {
		                  sh 'docker build -t app .'
                      sh "docker tag app:latest almaha96/capstone"
                      sh 'docker push almaha96/capstone'
                  }
              }
         }
         

      stage('Create kubeconfig') {
        steps {  
          withAWS(region:'us-west-2',credentials:'aws-static') {
            sh 'aws eks --region us-west-2 update-kubeconfig --name CapstoneCluster'  
           }
        }
      }

      stage('Deploy containers') {
        steps {
          withAWS(region:'us-west-2',credentials:'aws-static') {
            sh "kubectl set image deployment/capstone-deploy container-deploy=almaha96/capstone:latest"
            sh 'kubectl apply -f deployment/deployments.yml'  
            sh "kubectl get nodes"
            sh "kubectl get deployment"
            sh "kubectl get pod -o wide"
            sh "kubectl get service/capstone-service"
           }
        }
      } 

     
  }
}
