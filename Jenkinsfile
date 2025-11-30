pipeline {
    agent any

    tools {
        maven 'Maven' // if Maven installed
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<yourname>/<yourrepo>.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh """
                        mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=webapp \
                        -Dsonar.projectName=WebAppProject \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=$SONARQUBE_AUTH_TOKEN
                    """
                }
            }
        }
    }
}
