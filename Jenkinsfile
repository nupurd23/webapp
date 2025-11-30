pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/nupurd23/webapp.git', branch: 'develop'
            }
        }

        stage('Build Project') {
            steps {
                echo 'Building the Web Application...'
                // example build command:
                // sh 'mvn -DskipTests clean package'
            }
        }

        stage('Test Project') {
            steps {
                echo 'Running tests...'
                // example test command:
                // sh 'mvn test'
            }
        }

        stage('Deploy Project') {
            steps {
                echo 'Deploying application...'
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
stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv('SonarQube') {
            sh """
                mvn clean verify sonar:sonar \
                -Dsonar.projectKey=webapp \
                -Dsonar.host.url=http://localhost:9000 \
                -Dsonar.login=$SONARQUBE_AUTH_TOKEN
            """
        }
    }
}

