pipeline {
    agent any
    stages {
        stage('Git Checkout Stage') {
            steps {
                git branch: 'prod' , credentialsId: 'git-cred' , url: 'https://github.com/bkrrajmali/java-springboot-app1.git'

            }
        }
    }
}