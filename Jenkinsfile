pipeline {
    agent any
    tools {
        maven 'maven3'
    }
        stages {
        stage('Git Checkout') {
            steps {
                git branch: 'prod' , credentialsId: 'git-cred', url: 'https://github.com/teju12b5/aws-cicd-evening.git'
            }
        }
        stage('Maven Compile') {
            steps {
               echo 'Maven Compile Started'
               sh 'mvn compile'
            }
        } 
         stage('Maven Test') {
            steps {
               echo 'Maven Test Started'
               sh 'mvn test'
            }
        } 
        stage('File System Scan by Trivy') {
            steps {
               echo 'Trivy Scan Started'
               sh 'trivy fs --format table --output trivy-fs-output.txt .'
            }
        } 
            stage('Maven Package') {
            steps {
               echo 'Maven package Started'
               sh 'mvn package'
          }
        } 
    }
}        