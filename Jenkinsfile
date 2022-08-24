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
                      -Dsonar.host.url=http://65.0.31.80:9000 \
                      -Dsonar.login=d644ac90ab3bc2b35853d52e9fc2d986dbec90df'
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

