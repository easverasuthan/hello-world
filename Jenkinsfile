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
            }

         }
    }   
}
