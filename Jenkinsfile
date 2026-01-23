pipeline {
    agent any

    tools {
        jdk 'jdk21'
        sonarQubeScanner 'sonar-scanner'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=ashwin918_Jenkins-demo-pipelines \
                        -Dsonar.organization=ashwin918 \
                        -Dsonar.host.url=https://sonarcloud.io
                    '''
                }
            }
        }
    }
}
