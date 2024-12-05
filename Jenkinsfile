pipeline {
    agent any
    tools{
        maven 'maven3'
    }
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
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
        stage('Maven test') {
            steps {
                echo 'Maven test Started'
                sh 'mvn test'
                echo 'Maven test Finished'
            }
        }
        stage ('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=BoardGame -Dsonar.projectKey=BoardGame \
                    -Dsonar.java.binaries=. -Dsonar.exclusions=**/trivy-image-report.html'''
                }
            }
        }
        stage('Quality Gate') {
            steps {
                script {
                timeout(time: 1, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true, credentialsId: 'sonar'
                }
              }
            }
        }
    }
}
