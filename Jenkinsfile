pipeline {
    agent any
    
    tools{
        maven 'Maven-3.9.9'
    }
    stages {
        stage('clone') {
            steps {
              git 'https://github.com/SheetalKadolkar/maven-web-app-master.git'
            }
        }
        stage('build'){
            steps{
                 sh 'mvn clean package'
            }
        }
        stage('docker image'){
            steps {
                sh 'docker build -t sheetalkadolkar/mavenwebapp .'
            }
        }
        stage('k8s deploy'){
            steps{
               sh 'kubectl apply -f k8s-deploy.yml'
            }
        }
    }
}
