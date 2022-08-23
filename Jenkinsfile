pipeline {
    agent any

    tools {
        maven 'Maven 3.0.5'  
    }

    stages {
        stage('clone') {
            steps {
              git credentialsId: 'ssh_key', url: 'https://github.com/kesav-devops/ks.git'
            }
            }  
        stage('clean') {
            steps {
               sh 'mvn clean'               
            }
            }
         stage('validate') {
            steps {
                sh 'mvn validate'
            }
            } 
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
            }
         stage('package') {
            steps {
                sh 'mvn package'
            }
            }
         stage('deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}

