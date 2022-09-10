pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  
    }

    stages {
        stage('clone') {
            steps {
              git credentialsId: 'ssh_key', url: 'https://github.com/kesav-devops/ks.git'
            }
            }
        stage('maven version') {
            steps {
               sh 'mvn --version'               
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
        stage('sonarQube scan') {
            steps {
                sh 'mvn sonar:sonar \
                      -Dsonar.host.url=http://3.108.191.185:9000 \
                      -Dsonar.login=097561b8f61b4c76d20d4b1e877819febeecfbd5'	
                                     
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

