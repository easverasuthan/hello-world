pipeline {

    agent {
        node {
            label 'slave_node1'
        }
    }
    stages {
        
        stage('Code Checkout') {
            steps {
             checkout scm
            }
        }
         stage ('Deploying our Api'){
            steps{
             checkout scm
             sh 'docker build -t hello-world .'
             sh 'docker tag hello-world 603389930669.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest'
             sh '$(aws ecr get-login --no-include-email --region us-east-1) > /dev/null'
             sh 'docker push 603389930669.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest'
             sh 'aws ecs update-service --cluster pratilipi --service hello-world --force-new-deployment --region us-east-1'
            }

         }
    }   
}
