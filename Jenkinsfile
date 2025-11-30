pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/nupurd23/webapp.git', branch: 'develop'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat """
                        "C:\\apache-maven-3.9.11\\bin\\mvn.cmd" clean verify sonar:sonar ^
                        -Dsonar.projectKey=webapp ^
                        -Dsonar.host.url=http://localhost:9000
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
