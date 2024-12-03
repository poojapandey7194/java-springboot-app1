pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'prod' , credentialsId: 'git-cred' , url: 'https://github.com/poojapandey7194/java-springboot-app1.git'

            }
        }
    }
}
