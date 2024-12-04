pipeline {
    agent any
    tools{
        maven 'maven3'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'prod' , credentialsId: 'git-cred' , url: 'https://github.com/poojapandey7194/java-springboot-app1.git'
            }
        }
        stage('Maven Compile') {
            steps {
                echo 'Maven Compile Started'
                sh 'mvn compile'
                echo 'Maven Compile Finished'
            }
        }
    }
}
