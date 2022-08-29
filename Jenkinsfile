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
                      -Dsonar.host.url=http://13.233.224.189:9000 \
                      -Dsonar.login=3573a1788c725e2106e4366a1b5afc5d49d77b8c'
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

