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
                      -Dsonar.login=3fd9b1c6e191bfb06f5495249c941305c6e36866'
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

