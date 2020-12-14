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
             sh 'docker tag hello-world 122974644486.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest'
             sh '$(aws ecr get-login --no-include-email --region us-east-1)'
             sh 'docker push 122974644486.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest'
            }

         }
    }   
}
