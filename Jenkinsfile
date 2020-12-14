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
             sh 'docker build --build-arg ACCESS_TOKEN_USR --build-arg ACCESS_TOKEN_PWD -t hello-world .'
             sh 'docker tag hello-world 122974644486.dkr.ecr.us-east-2.amazonaws.com/hello-world:latest'
             sh '$(aws ecr get-login --no-include-email --region us-east-1)'
             sh 'docker push 122974644486.dkr.ecr.us-east-2.amazonaws.com/hello-world:latest'
            }

         }
    }   
}
